---
title: Exécution d’opérations asynchrones | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- initialization [SQL Server Native Client]
- database connections [SQL Server Native Client]
- data access [SQL Server Native Client], asynchronous operations
- connections [SQL Server Native Client]
- asynchronous operations [SQL Server Native Client]
- rowsets [SQL Server], initializing
- SQLNCLI, asynchronous operations
- SQL Server Native Client, asynchronous operations
ms.assetid: 8fbd84b4-69cb-4708-9f0f-bbdf69029bcc
caps.latest.revision: 45
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9d437129005334a3db9994309e5dd0b275435689
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2018
ms.locfileid: "40393212"
---
# <a name="performing-asynchronous-operations"></a>Exécution d'opérations asynchrones
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] permet aux applications d'effectuer des opérations de base de données asynchrones. Le traitement asynchrone permet aux méthodes d'être retournées immédiatement sans blocage du thread appelant. Cela rend le multithreading plus puissant et plus souple, sans obliger le développeur à créer explicitement des threads ou à gérer la synchronisation. Les applications requièrent un traitement asynchrone lors de l'initialisation d'une connexion de base de données, ou lors de l'initialisation du résultat de l'exécution d'une commande.  
  
## <a name="opening-and-closing-a-database-connection"></a>Ouverture et fermeture d'une connexion de base de données  
 Lorsque vous utilisez le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] fournisseur OLE DB Native Client, les applications conçues pour initialiser un objet de source de données de façon asynchrone peuvent définir DBPROPVAL_ASYNCH_INITIALIZE dans la propriété DBPROP_INIT_ASYNCH avant d’appeler  **IDBInitialize::Initialize**. Quand cette propriété est définie, le fournisseur est retourné immédiatement à partir de l’appel à **Initialize** avec la valeur S_OK si l’opération s’est effectuée immédiatement ou DB_S_ASYNCHRONOUS si l’initialisation se poursuit de façon asynchrone. Applications peuvent interroger le **IDBAsynchStatus** ou [ISSAsynchStatus](../../native-client-ole-db-interfaces/issasynchstatus-ole-db.md)interface sur l’objet de source de données, puis appelez **IDBAsynchStatus::GetStatus** ou[ ISSAsynchStatus::WaitForAsynchCompletion](../../native-client-ole-db-interfaces/issasynchstatus-waitforasynchcompletion-ole-db.md) pour obtenir l’état de l’initialisation.  
  
 De plus, la propriété SSPROP_ISSAsynchStatus a été ajoutée au jeu de propriétés DBPROPSET_SQLSERVERROWSET. Les fournisseurs qui prennent en charge l’interface **ISSAsynchStatus** doivent implémenter cette propriété avec la valeur VARIANT_TRUE.  
  
 **IDBAsynchStatus::Abort** ou [ISSAsynchStatus::Abort](../../native-client-ole-db-interfaces/issasynchstatus-abort-ole-db.md) peut être appelée pour annuler l’appel asynchrone à **Initialize**. Le consommateur doit demander explicitement l'initialisation de la source de données asynchrone. Sinon, **IDBInitialize::Initialize** n’est pas retournée tant que l’objet source de données n’est pas complètement initialisé.  
  
> [!NOTE]  
>  Objets de source de données utilisés pour le regroupement de connexions ne peut pas appeler le **ISSAsynchStatus** interface dans le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif. L’interface **ISSAsynchStatus** n’est pas exposée pour les objets sources de données regroupés.  
>   
>  Si une application force explicitement l’utilisation du moteur de curseur, **IOpenRowset::OpenRowset** et **IMultipleResults::GetResult** ne prennent pas en charge le traitement asynchrone.  
>   
>  En outre, la dll de proxy/stub de communication à distance (dans MDAC 2.8) ne peut pas appeler le **ISSAsynchStatus** dans l’interface [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client. L’interface **ISSAsynchStatus** n’est pas exposée via la communication à distance.  
>   
>  Les composants du service ne prennent pas en charge **ISSAsynchStatus**.  
  
## <a name="execution-and-rowset-initialization"></a>Exécution et initialisation de l'ensemble de lignes  
 Les applications conçues pour ouvrir de façon asynchrone le résultat de l'exécution d'une commande peuvent définir DBPROPVAL_ASYNCH_INITIALIZE dans la propriété DBPROP_ROWSET_ASYNCH. Lors de la définition de ce bit avant d’appeler **IDBInitialize::Initialize**, **ICommand::Execute**, **IOpenRowset::OpenRowset** ou **IMultipleResults::GetResult**, l’argument *riid* doit avoir pour valeur IID_IDBAsynchStatus, IID_ISSAsynchStatus ou IID_IUnknown.  
  
 La méthode est retournée immédiatement avec S_OK si l’initialisation de l’ensemble de lignes s’effectue immédiatement (ou avec DB_S_ASYNCHRONOUS si l’ensemble de lignes poursuit son initialisation de façon asynchrone) avec *ppRowset* défini en fonction de l’interface demandée sur l’ensemble de lignes. Pour le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] fournisseur OLE DB Native Client, cette interface peut faire que **IDBAsynchStatus** ou **ISSAsynchStatus**. Jusqu’à ce que l’ensemble de lignes soit entièrement initialisé, cette interface se comporte comme si elle était dans un état suspendu ; par ailleurs, l’appel de **QueryInterface** pour les interfaces autres **qu’IID_IDBAsynchStatus** ou **qu’IID_ISSAsynchStatus** peut retourner E_NOINTERFACE. À moins que le consommateur ne demande explicitement un traitement asynchrone, l'ensemble de lignes est initialisé de façon synchrone. Toutes les interfaces demandées sont disponibles quand **IDBAsynchStaus::GetStatus** ou **ISSAsynchStatus::WaitForAsynchCompletion** est retournée avec l’indication que l’opération asynchrone a été effectuée. Cela ne signifie pas nécessairement que l'ensemble de lignes soit entièrement rempli, mais il est prêt et complètement fonctionnel.  
  
 Si la commande exécutée ne retourne pas d’ensemble de lignes, elle est quand même retournée immédiatement avec un objet qui prend en charge **IDBAsynchStatus**.  
  
 S'il vous faut obtenir plusieurs résultats à partir de l'exécution d'une commande asynchrone, vous devez :  
  
-   définir DBPROPVAL_ASYNCH_INITIALIZE dans la propriété DBPROP_ROWSET_ASYNCH, avant d'exécuter la commande ;  
  
-   appeler **ICommand::Execute** et demander **IMultipleResults**.  
  
 Les interfaces **IDBAsynchStatus** et **ISSAsynchStatus** peuvent ensuite être obtenues en interrogeant l’interface de résultats multiples via **QueryInterface**.  
  
 Quand l’exécution de la commande est terminée, **IMultipleResults** peut être utilisé normalement à une exception près par rapport au traitement synchrone : DB_S_ASYNCHRONOUS peut être retourné, auquel cas **IDBAsynchStatus** ou **ISSAsynchStatus** peut être utilisée pour déterminer le moment où l’opération est achevée.  
  
## <a name="examples"></a>Exemples  
 Dans l'exemple suivant, l'application appelle une méthode non bloquante, effectue d'autres traitements, puis retourne au traitement des résultats. **ISSAsynchStatus::WaitForAsynchCompletion** attend l’objet d’événement interne jusqu’à ce que l’opération s’exécutant de manière asynchrone soit terminée ou que le délai spécifié par *dwMilisecTimeOut* soit passé.  
  
```  
// Set the DBPROPVAL_ASYNCH_INITIALIZE bit in the   
// DBPROP_ROWSET_ASYNCH property before calling Execute().  
  
DBPROPSET CmdPropset[1];  
DBPROP CmdProperties[1];  
  
CmdPropset[0].rgProperties = CmdProperties;  
CmdPropset[0].cProperties = 1;  
CmdPropset[0].guidPropertySet = DBPROPSET_ROWSET;  
  
// Set asynch mode for command.  
CmdProperties[0].dwPropertyID = DBPROP_ROWSET_ASYNCH;  
CmdProperties[0].vValue.vt = VT_I4;  
CmdProperties[0].vValue.lVal = DBPROPVAL_ASYNCH_INITIALIZE;  
CmdProperties[0].dwOptions = DBPROPOPTIONS_REQUIRED;  
  
hr = pICommandProps->SetProperties(1, CmdPropset);  
  
hr = pICommand->Execute(  
   pUnkOuter,  
   IID_ISSAsynchStatus,  
   pParams,  
   pcRowsAffected,  
   (IUnknown**)&pISSAsynchStatus);  
  
if (hr == DB_S_ASYNCHRONOUS)  
{  
   // Do some work here...  
  
   hr = pISSAsynchStatus->WaitForAsynchCompletion(dwMilisecTimeOut);  
   if ( hr == S_OK)  
   {  
      hr = pISSAsynchStatus->QueryInterface(IID_IRowset, (void**)&pRowset);  
      pISSAsynchStatus->Release();  
   }  
}  
```  
  
 **ISSAsynchStatus::WaitForAsynchCompletion** attend l’objet d’événement interne jusqu’à ce que l’opération s’exécutant de manière asynchrone soit terminée ou que la valeur *dwMilisecTimeOut* soit passée.  
  
 L'exemple suivant illustre le traitement asynchrone avec plusieurs jeux de résultats :  
  
```  
DBPROP CmdProperties[1];  
  
// Set asynch mode for command.  
CmdProperties[0].dwPropertyID = DBPROP_ROWSET_ASYNCH;  
CmdProperties[0].vValue.vt = VT_I4;  
CmdProperties[0].vValue.lVal = DBPROPVAL_ASYNCH_INITIALIZE;  
  
hr = pICommand->Execute(  
   pUnkOuter,  
   IID_IMultipleResults,  
   pParams,  
   pcRowsAffected,  
   (IUnknown**)&pIMultipleResults);  
  
// Use GetResults for ISSAsynchStatus.  
hr = pIMultipleResults->GetResult(IID_ISSAsynchStatus, (void **) &pISSAsynchStatus);  
  
if (hr == DB_S_ASYNCHRONOUS)  
{  
   // Do some work here...  
  
   hr = pISSAsynchStatus->WaitForAsynchCompletion(dwMilisecTimeOut);  
   if (hr == S_OK)  
   {  
      hr = pISSAsynchStatus->QueryInterface(IID_IRowset, (void**)&pRowset);  
      pISSAsynchStatus->Release();  
   }  
}  
```  
  
 Pour empêcher tout blocage, le client peut vérifier l'état d'une opération asynchrone en cours d'exécution, comme le montre l'exemple suivant :  
  
```  
// Set the DBPROPVAL_ASYNCH_INITIALIZE bit in the   
// DBPROP_ROWSET_ASYNCH property before calling Execute().  
hr = pICommand->Execute(  
   pUnkOuter,  
   IID_ISSAsynchStatus,  
   pParams,  
   pcRowsAffected,  
   (IUnknown**)&pISSAsynchStatus);   
  
if (hr == DB_S_ASYNCHRONOUS)  
{  
   do{  
      // Do some work...  
      hr = pISSAsynchStatus->GetStatus(DB_NULL_HCHAPTER, DBASYNCHOP_OPEN, NULL, NULL, &ulAsynchPhase, NULL);  
   }while (DBASYNCHPHASE_COMPLETE != ulAsynchPhase)  
   if SUCCEEDED(hr)  
   {  
      hr = pISSAsynchStatus->QueryInterface(IID_IRowset, (void**)&pRowset);  
   }  
   pIDBAsynchStatus->Release();  
}  
```  
  
 L'exemple suivant montre comment vous pouvez annuler l'opération asynchrone en cours d'exécution :  
  
```  
// Set the DBPROPVAL_ASYNCH_INITIALIZE bit in the   
// DBPROP_ROWSET_ASYNCH property before calling Execute().  
hr = pICommand->Execute(  
   pUnkOuter,  
   IID_ISSAsynchStatus,  
   pParams,  
   pcRowsAffected,  
   (IUnknown**)&pISSAsynchStatus);  
  
if (hr == DB_S_ASYNCHRONOUS)  
{  
   // Do some work...  
   hr = pISSAsynchStatus->Abort(DB_NULL_HCHAPTER, DBASYNCHOP_OPEN);  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctionnalités de SQL Server Native Client](sql-server-native-client-features.md)   
 [Propriétés et comportements de l’ensemble de lignes](../../native-client-ole-db-rowsets/rowset-properties-and-behaviors.md)   
 [ISSAsynchStatus &#40;OLE DB&#41;](../../native-client-ole-db-interfaces/issasynchstatus-ole-db.md)  
  
  
