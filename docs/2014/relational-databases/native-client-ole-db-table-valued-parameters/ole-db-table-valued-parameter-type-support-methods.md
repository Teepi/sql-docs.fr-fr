---
title: Support de Type paramètre table OLE DB (méthodes) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (OLE DB), API support (methods)
ms.assetid: e3c2a450-8fd4-44cb-93d8-affe1b65c68e
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: eebe58ccc32e7440505237730b062ff9b6056ef0
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37411218"
---
# <a name="ole-db-table-valued-parameter-type-support-methods"></a>Prise en charge des types de paramètre table OLE DB (méthodes)
  Les méthodes OLE DB standard suivantes prennent en charge les paramètres table :  
  
|Méthode|Prise en charge des paramètres table|  
|------------|-------------------------------------|  
|ITableDefinitionWithConstraints::CreateTableWithConstraints|Utilisée lorsque vous connaissez les informations de type du paramètre table, et que vous souhaitez instancier un objet d'ensemble de lignes de paramètre table en fonction des informations de type.<br /><br /> Pour plus d’informations, consultez « Scénario statique » dans [création d’ensemble de lignes de paramètres table-Valued](table-valued-parameter-rowset-creation.md).|  
|IOpenRowset::OpenRowset|Utilisée lorsque vous ne connaissez pas les informations de type d'un paramètre table, et que vous souhaitez instancier un objet d'ensemble de lignes de paramètre table en fonction des informations de métadonnées extraites du serveur.<br /><br /> Pour plus d’informations, consultez « Scénario dynamique » dans [création d’ensemble de lignes de paramètres table-Valued](table-valued-parameter-rowset-creation.md).|  
|ISSCommandWithParameters::SetParameterInfo|Pour spécifier un paramètre de commande de paramètre table, le consommateur Spécifie le type du paramètre en tant que « table » ou « DBTYPE_TABLE » dans le *pwszName* membre de la structure DBPARAMBINDINFO. Le *ulParamSize* est défini sur ~ 0. Pour plus d’informations, consultez « Spécification de paramètre table » dans [Executing Commands Containing Table-Valued paramètres](executing-commands-containing-table-valued-parameters.md).|  
|ISSCommandWithParameters::SetParameterProperties|Définit les propriétés spécifiques aux paramètres table, telles que le nom de schéma, le nom de type, l'ordre des colonnes et les colonnes par défaut.<br /><br /> Le consommateur spécifie la position ordinale du paramètre dans le *iOrdinal* de la structure SSPARAMPROPS. Le jeu de propriétés demandé est DBPROPSET_SQLSERVERPARAMETER.|  
|ISSCommandWithParameters::GetParameterInfo|Obtient les types de tous les paramètres d'une commande spécifiée.<br /><br /> Pour les paramètres table, le *wType* champ dans la structure DBPARAMINFO a type DBTYPE_TABLE. Le *ulParamSize* champ sera défini sur ~ 0 pour indiquer une longueur inconnue.|  
|ISSCommandWithParameters::GetParameterProperties|Obtient des informations de type supplémentaires pour les paramètres du type DBTYPE_TABLE.<br /><br /> Le consommateur spécifie la position ordinale du paramètre dans le *iOrdinal* membre de la structure SSPARAMPROPS. Le consommateur peut demander les propriétés dans le jeu de propriétés DBPROPSET_SQLSERVERPARAMETER qui sont répertoriées sous ISSCommandWithParameters::SetParameterProperties.<br /><br /> Dans la mesure où le consommateur ne connaît pas le type de paramètre table, le fournisseur doit définir SSPROP_PARAM_TYPE_TYPENAME, SSPROP_PARAM_TYPE_SCHEMANAME et SSPROP_PARAM_TYPE_CATALOGNAME sur leurs valeurs correctes. Les propriétés restantes, SSPROP_PARAM_TABLE_DEFAULT_COLUMNS et SSPROP_PARAM_TABLE_COLUMN_SORT_ORDER, utilisent leurs valeurs par défaut. Une fois que le consommateur a découvert le nom de type de paramètre table, il utilise IOpenRowset::OpenRowset pour créer une instance de ce paramètre table, en spécifiant le nom du type de paramètre table. Pour plus d’informations, consultez [découverte de Type de paramètre table-Valued](../../database-engine/dev-guide/table-valued-parameter-type-discovery.md).|  
|IRowsetInfo::GetProperties|Obtient les propriétés de l'ensemble de lignes de paramètre table. Le consommateur peut utiliser ces propriétés pour optimiser la configuration des liaisons.|  
|IColumnsRowset::GetColumnsRowset|Récupère les informations de métadonnées relatives une table [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour les paramètres table, cette même interface fournit des informations de métadonnées détaillées à propos de chaque colonne, notamment les suivantes :<br /><br /> -DBCOLUMN_FLAGS indique la possibilité de valeur null via le bit DBCOLUMNFLAGS_ISNULLABLE.<br />-DBCOLUMN_ISUNIQUE indique si la colonne est une colonne d’identité.<br />-DBCOLUMN_COMPUTEMODE indique si la colonne est calculée.|  
|IAccessor::CreateAccessor|Pour lier un objet d’ensemble de lignes de paramètre table à un paramètre de commande, vous créez un accesseur avec son *wType* membre a la valeur DBTYPE_TABLE. La structure DBOBJECT contiendra IID_IRowset ou toute autre interface objet ensemble de lignes valide dans le *iid* membre. Les autres champs sont traités de la même façon que DBTYPE_IUNKNOWN.|  
  
## <a name="see-also"></a>Voir aussi  
 [Prise en charge de Type de paramètre table OLE DB](ole-db-table-valued-parameter-type-support.md)   
 [Création d’ensemble de lignes de paramètre table](table-valued-parameter-rowset-creation.md)   
 [Utiliser des paramètres table &#40;OLE DB&#41;](table-valued-parameters-ole-db.md)  
  
  
