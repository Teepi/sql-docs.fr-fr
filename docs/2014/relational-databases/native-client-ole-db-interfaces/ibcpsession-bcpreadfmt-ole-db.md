---
title: IBCPSession::BCPReadFmt (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- IBCPSession::BCPReadFmt (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- BCPReadFmt method
ms.assetid: e2a12050-94e4-48a3-8a48-b780d646f116
caps.latest.revision: 26
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: aa0f1501955db61889bb437e545cda95dfe8b31f
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37428255"
---
# <a name="ibcpsessionbcpreadfmt-ole-db"></a>IBCPSession::BCPReadFmt (OLE DB)
  Lit les informations de format pour chaque colonne à partir du fichier de format.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
HRESULT BCPReadFmt(   
const wchar_t *pwszFormatFile);  
```  
  
## <a name="remarks"></a>Notes  
 La méthode **BCPReadFmt** est utilisée pour lire les données d'un fichier de format qui spécifie le format des données dans le fichier de données. Cette méthode est capable de détecter la version correcte du fichier de format. Elle peut détecter automatiquement si le fichier de format est au format xml ou dans un ancien format et qu'il se comporte en conséquence. Les versions de fichier de format pris en charge par le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur natif OLE DB du Client BCP sont 6.0 ou version ultérieure.  
  
 Après le **BCPReadFmt** méthode lit les valeurs de format, il effectue les appels appropriés pour le [IBCPSession::BCPColumns](ibcpsession-bcpcolumns-ole-db.md) et [IBCPSession::BCPColFmt](ibcpsession-bcpcolfmt-ole-db.md) méthodes. L'utilisateur n'a pas besoin d'analyser un fichier de format et d'effectuer ces appels.  
  
 Pour enregistrer un fichier de format, appelez le [IBCPSession::BCPWriteFmt](ibcpsession-bcpwritefmt-ole-db.md) (méthode). Les appels à la méthode **BCPReadFmt** peuvent référencer des formats enregistrés. L'utilitaire**bcp**peut également enregistrer des formats de données définis par l'utilisateur dans des fichiers qui peuvent être référencés par la méthode **BCPReadFmt** .  
  
 Le `BCP_OPTION_DELAYREADFMT` valeur de la *eOption* paramètre de [IBCPSession::BCPControl](ibcpsession-bcpcontrol-ole-db.md) modifie le comportement de IBCPSession::BCPReadFmt.  
  
## <a name="arguments"></a>Arguments  
 *pwszFormatFile*[in]  
 Chemin d'accès et nom du fichier contenant les valeurs de format du fichier de données.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 Cette méthode signale les erreurs en attribuant à la propriété Nombre de l'objet Err global l'une des valeurs du tableau suivant.  
 S_OK  
  
 E_FAIL  
 Une erreur spécifique au fournisseur s’est produite, pour des informations détaillées, utilisez le [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) interface.  
  
 E_OUTOFMEMORY  
 Erreur de mémoire insuffisante.  
  
 E_UNEXPECTED  
 L'appel à la méthode était inattendu. Par exemple, le [IBCPSession::BCPInit](ibcpsession-bcpinit-ole-db.md) (méthode) n’a pas été appelée avant d’appeler cette méthode.  
  
## <a name="see-also"></a>Voir aussi  
 [IBCPSession &#40;OLE DB&#41;](ibcpsession-ole-db.md)   
 [Exécution d'opérations de copie en bloc](../native-client/features/performing-bulk-copy-operations.md)  
  
  
