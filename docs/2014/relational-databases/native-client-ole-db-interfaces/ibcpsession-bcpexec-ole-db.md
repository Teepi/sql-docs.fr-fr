---
title: IBCPSession::BCPExec (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- IBCPSession::BCPExec (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- BCPExec method
ms.assetid: 0f4ebb63-cf03-4e53-846e-6c3021cde007
caps.latest.revision: 23
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: eb0c10e4c12bba99225bc5f332a8ad6701de29fd
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37414028"
---
# <a name="ibcpsessionbcpexec-ole-db"></a>IBCPSession::BCPExec (OLE DB)
  Effectue l'opération de copie en bloc.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
HRESULT BCPExec(   
DBROWCOUNT *pRowsCopied);  
```  
  
## <a name="remarks"></a>Notes  
 Le **BCPExec** méthode copie les données à partir d’un fichier utilisateur vers une table de base de données ou vice versa, selon la valeur de la *eDirection* paramètre utilisé avec le [IBCPSession::BCPInit](ibcpsession-bcpinit-ole-db.md)(méthode).  
  
 Avant d'appeler **BCPExec**, appelez la méthode **BCPInit** avec un nom de fichier utilisateur valide. L'échec de cette opération entraîne une erreur. La seule exception est si une requête doit être utilisée pour une opération de copie en bloc sortante. Dans ce cas, spécifiez NULL pour le nom de table dans la méthode **BCPInit** , puis spécifiez la requête à l'aide de l'option BCP_OPTION_HINTS.  
  
 La méthode **BCPExec** est la seule méthode de copie en bloc qui est susceptible d'être en attente pendant une durée prolongée. Il s'agit par conséquent de la seule méthode de copie en bloc qui prend en charge le mode asynchrone. Pour utiliser le mode asynchrone, affectez la valeur VARIANT_TRUE à la propriété de session spécifique au fournisseur SSPROP_ASYNCH_BULKCOPY avant d'appeler la méthode **BCPExec** . Cette propriété est disponible dans le jeu de propriétés DBPROPSET_SQLSERVERSESSION. Pour tester l'achèvement, appelez la méthode **BCPExec** avec les mêmes paramètres. Si la copie en bloc n'est pas encore terminée, la méthode **BCPExec** retourne DB_S_ASYNCHRONOUS. Elle retourne également dans l'argument *pRowsCopied* le nombre de lignes qui ont été envoyées ou reçues à partir du serveur. Les lignes envoyées au serveur sont validées uniquement une fois la fin du lot atteinte.  
  
## <a name="arguments"></a>Arguments  
 *pRowsCopied*[out]  
 Pointeur vers une valeur DWORD. La méthode **BCPExec** remplit la valeur DWORD avec le nombre de lignes copiées avec succès. Si l'argument *pRowsCopied* a la valeur NULL, il est ignoré par la méthode **BCPExec** .  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 Cette méthode signale les erreurs en attribuant à la propriété Nombre de l'objet Err global l'une des valeurs du tableau suivant.  
 S_OK  
  
 E_FAIL  
 Une erreur spécifique au fournisseur s’est produite ; Pour plus d’informations, utilisez le [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) interface.  
  
 E_UNEXPECTED  
 L'appel à la méthode était inattendu. Par exemple, la méthode **BCPInit** n'a pas été appelée avant cette méthode. Se produit également si l'opération a été abandonnée suite à l'utilisation de l'option BCP_OPTION_ABORT et que la méthode **BCPExec** a été appelée ensuite.  
  
 E_OUTOFMEMORY  
 Erreur de mémoire insuffisante.  
  
 DB_S_ENDOFROWSET  
 L'opération de copie en bloc s'est terminée et tout le transfert de données a été effectué.  
  
 DB_S_ASYNCHRONOUS  
 Le lot actuel de lignes a été copié. Rappelez la méthode **BCPExec** pour transférer le lot suivant.  
  
 DB_S_ERRORSOCCURRED  
 Des erreurs se sont produites pendant l'opération de copie en bloc et certaines lignes n'ont pas pu être copiées. Le nombre d'erreurs est inférieur au nombre maximal d'erreurs autorisé.  
  
## <a name="see-also"></a>Voir aussi  
 [IBCPSession &#40;OLE DB&#41;](ibcpsession-ole-db.md)   
 [Exécution d'opérations de copie en bloc](../native-client/features/performing-bulk-copy-operations.md)  
  
  
