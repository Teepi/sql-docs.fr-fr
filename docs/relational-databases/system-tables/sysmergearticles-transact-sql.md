---
title: sysmergearticles (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sysmergearticles
- sysmergearticles_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysmergearticles system table
ms.assetid: e9b1648e-4660-4688-9f56-18b2baf7228c
caps.latest.revision: 37
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 8d9b089f7001c556e08637de5518320ee211bb55
ms.sourcegitcommit: a431ca21eac82117492d7b84c398ddb3fced53cc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39102607"
---
# <a name="sysmergearticles-transact-sql"></a>sysmergearticles (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contient une ligne pour chaque article de fusion défini dans la base de données locale. Cette table est stockée dans la base de données de publication.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**nom**|**sysname**|Nom de l'article.|  
|**type**|**tinyint**|Indique le type d'article, qui peut être l'un des suivants :<br /><br /> **10** = table.<br /><br /> **32** = procédure stockée (schéma uniquement).<br /><br /> **64** = vue ou vue indexée (schéma uniquement).<br /><br /> **128** = fonction définie par l’utilisateur (schéma uniquement).<br /><br /> **160** = synonyme (schéma uniquement).|  
|**objid**|**Int**|L’identificateur d’objet.|  
|**sync_objid**|**Int**|ID d'objet de la vue représentant l'ensemble de données synchronisées.|  
|**view_type**|**tinyint**|Type de vue :<br /><br /> **0** ne = pas d’une vue ; utilisez l’intégralité de l’objet de base.<br /><br /> **1** = vue permanente.<br /><br /> **2** = vue temporaire.|  
|**artid**|**uniqueidentifier**|Numéro d'identification unique de l'article donné.|  
|**description**|**nvarchar(255)**|Brève description de l'article.|  
|**pre_creation_command**|**tinyint**|L’action par défaut à effectuer lorsque l’article est créé dans la base de données d’abonnement :<br /><br /> **0 =** aucune - si la table existe déjà sur l’abonné, aucune action n’est effectuée.<br /><br /> **1** = Supprimer - supprime la table avant de créer à nouveau.<br /><br /> **2** = supprimer-entraîne une suppression basée sur la clause WHERE dans le filtre de sous-ensemble.<br /><br /> **3** = tronquer-identique **2**, mais supprime des pages au lieu de lignes. Toutefois, n'accepte pas la clause WHERE.|  
|**pubid**|**uniqueidentifier**|ID de la publication à laquelle appartient l'article actif.|  
|**surnom**|**Int**|Le mappage de surnom pour l'identification de l'article.|  
|**column_tracking**|**Int**|Indique si le suivi des colonnes est implémentée pour l’article.|  
|**status**|**tinyint**|Indique l'état de l'article, qui peut être l'un des suivants :<br /><br /> **1** = Unsynced - le script de traitement initial pour publier la table sera exécuté lors de la prochaine exécution de l’Agent d’instantané.<br /><br /> **2** = active - le script de traitement initial pour publier la table a été exécuté.<br /><br /> **5** = New_inactive - à ajouter.<br /><br /> **6** = New_active - à ajouter.|  
|**conflict_table**|**sysname**|Nom de la table locale qui contient les enregistrements en conflit pour l'article actif. Cette table est fournie à titre d'information uniquement et son contenu peut être modifié ou supprimé à l'aide des routines personnalisées de résolution de conflits ou directement par l'administrateur.|  
|**creation_script**|**nvarchar(255)**|Script de création de l'article.|  
|**conflict_script**|**nvarchar(255)**|Script de conflit de l'article.|  
|**article_resolver**|**nvarchar(255)**|Outil personnalisé de résolution des conflits au niveau ligne pour l'article.|  
|**ins_conflict_proc**|**sysname**|La procédure utilisée pour écrire les conflits dans **conflict_table**.|  
|**insert_proc**|**sysname**|Procédure utilisée par l'outil de résolution des conflits pour insérer des lignes lors de la synchronisation.|  
|**update_proc**|**sysname**|Procédure utilisée par l'outil de résolution des conflits pour mettre à jour des lignes lors de la synchronisation.|  
|**select_proc**|**sysname**|Nom de la procédure stockée générée automatiquement que l'Agent de fusion utilise pour effectuer le verrouillage et rechercher les colonnes et les lignes d'un article.|  
|**metadata_select_proc**|**sysname**|Le nom de la procédure stockée générée automatiquement, permettant d’accéder aux métadonnées dans les tables système de réplication de fusion.|  
|**delete_proc**|**sysname**|Procédure utilisée par l'outil de résolution des conflits pour supprimer des lignes lors de la synchronisation.|  
|**schema_option**|**binary(8)**|Pour les valeurs prises en charge de *schema_option*, consultez [sp_addmergearticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md).|  
|**destination_object**|**sysname**|Nom de la table créée sur l'Abonné.|  
|**destination_owner**|**sysname**|Le nom du propriétaire de l’objet de destination.|  
|**resolver_clsid**|**nvarchar(50)**|ID de l'outil personnalisé de résolution des conflits|  
|**subset_filterclause**|**nvarchar(1000)**|Clause de filtre de l'article.|  
|**missing_col_count**|**Int**|Nombre de colonnes manquantes.|  
|**missing_cols**|**varbinary(128)**|Bitmap des colonnes manquantes.|  
|**excluded_cols**|**varbinary(128)**|Bitmap des colonnes exclues de l'article lors de son envoi à l'Abonné.|  
|**excluded_col_count**|**Int**|Nombre de colonnes exclues.|  
|**columns**|**varbinary(128)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**deleted_cols**|**varbinary(128)**|Bitmaps des colonnes supprimées dans la table source.|  
|**resolver_info**|**nvarchar(255)**|Espace de stockage réservé aux informations complémentaires nécessaires aux outils personnalisés de résolution des conflits.|  
|**view_sel_proc**|**nvarchar(290)**|Nom de la procédure stockée utilisée par l'Agent de fusion pour effectuer le remplissage initial d'un article dans une publication filtrée dynamiquement et pour énumérer les lignes modifiées d'une publication filtrée.|  
|**gen_cur**|**Int**|Numéro de génération des modifications locales apportées à la table de base d'un article.|  
|**vertical_partition**|**Int**|Indique si le filtrage de colonne est activé sur un article de table. **0** indique l’absence de filtrage vertical et publie toutes les colonnes.|  
|**identity_support**|**Int**|Spécifie si la gestion automatique de plages d'identités est activée. **1** signifie que la gestion de plage d’identités est activée, et **0** signifie qu’il n’existe aucune identité de la plage prise en charge.|  
|**before_image_objid**|**Int**|ID d'objet de la table de suivi. La table de suivi contient certaines valeurs de colonnes clés lorsqu’une publication est créée avec *@keep_partition_changes*  =  **true**.|  
|**before_view_objid**|**Int**|ID d'objet d'une table de vue. La vue est associée à une table qui détermine si une ligne appartenait à un Abonné particulier avant sa suppression ou sa mise à jour. S’applique uniquement lorsqu’une publication est créée avec *@keep_partition_changes*  =  **true.**|  
|**verify_resolver_signature**|**Int**|Spécifie si une signature numérique est vérifiée avant d'utiliser un résolveur dans une réplication de fusion :<br /><br /> **0** = signature n’est pas vérifiée.<br /><br /> **1** = signature est vérifiée pour déterminer s’il est d’une source approuvée.|  
|**allow_interactive_resolver**|**bit**|Spécifie si l'utilisation du composant résolveur interactif sur un article est activée. **1** Spécifie que le composant résolveur interactif est utilisé sur l’article.|  
|**fast_multicol_updateproc**|**bit**|Spécifie si l'Agent de fusion est activé pour appliquer des modifications à plusieurs colonnes d'une même ligne à partir d'une seule instruction UPDATE.<br /><br /> **0** = émet une instruction UPDATE distincte pour chaque colonne modifiée.<br /><br /> **1** = émet une instruction UPDATE qui provoque la mise à jour de plusieurs colonnes dans une instruction.|  
|**check_permissions**|**Int**|Bitmap des autorisations de niveau table, qui est vérifiée lorsque l'Agent de fusion applique les modifications au serveur de publication. *check_permissions* peut avoir une des valeurs suivantes :<br /><br /> **0 x 00 =** autorisations ne sont pas vérifiées.<br /><br /> **0 x 10 =** autorisations sont vérifiées sur le serveur de publication avant de pouvoir télécharger les insertions effectuées sur l’abonné.<br /><br /> **0 x 20 =** autorisations sont vérifiées sur le serveur de publication avant de pouvoir télécharger les mises à jour effectuées sur l’abonné.<br /><br /> **0 x 40 =** autorisations sont vérifiées sur le serveur de publication avant DELETE exécutées sur l’abonné puissent être téléchargées.|  
|**maxversion_at_cleanup**|**Int**|Génération la plus élevée pour laquelle les métadonnées sont nettoyées.|  
|**processing_order**|**Int**|Indique l’ordre de traitement des articles dans une publication de fusion ; sachant que la valeur **0** indiqué que l’article n’est pas ordonné, et les articles sont traités dans l’ordre à partir de la valeur la plus basse à la plus élevée. Si deux articles ont la même valeur, ils sont traités simultanément. Pour plus d’informations, consultez [Spécifier l’ordre de traitement d’articles de fusion](../../relational-databases/replication/merge/specify-the-processing-order-of-merge-articles.md).|  
|**upload_options**|**tinyint**|Définit des restrictions sur les mises à jour effectuées sur un Abonné ayant un abonnement client. Peut avoir une des valeurs suivantes.<br /><br /> **0** = il n’existe aucune restriction sur les mises à jour effectuées sur un abonné avec un abonnement client ; toutes les modifications sont téléchargées sur le serveur de publication.<br /><br /> **1** = les modifications sont autorisées sur un abonné disposant d’un abonnement client, mais elles ne sont pas téléchargées sur le serveur de publication.<br /><br /> **2** = les modifications ne sont pas autorisées sur un abonné avec un abonnement client.<br /><br /> Pour plus d’informations, consultez [Optimiser les performances de la réplication de fusion avec les articles en téléchargement seul](../../relational-databases/replication/merge/optimize-merge-replication-performance-with-download-only-articles.md).|  
|**published_in_tran_pub**|**bit**|Indique qu'un article d'une publication de fusion est également publié dans une publication transactionnelle.<br /><br /> **0** = l’article n’est pas publié dans un article transactionnel.<br /><br /> **1** = l’article est également publié dans un article transactionnel.|  
|**légère**|**bit**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**procname_postfix**|**nchar(32)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**well_partitioned_lightweight**|**bit**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**before_upd_view_objid**|**Int**|À ajouter.|  
|**delete_tracking**|**bit**|Indique si les suppressions sont répliquées.<br /><br /> **0** = suppressions ne sont pas répliquées.<br /><br /> **1** = les suppressions sont répliquées, ce qui est le comportement par défaut pour la réplication de fusion.<br /><br /> Lorsque la valeur de *delete_tracking* est **0**, de lignes supprimées sur l’abonné doivent être supprimées manuellement sur le serveur de publication et de lignes supprimées sur le serveur de publication doivent être supprimées manuellement sur l’abonné.<br /><br /> Remarque : Une valeur de **0** entraîne une non-convergence.|  
|**compensate_for_errors**|**bit**|Indique si les actions de compensation sont entreprises lorsque des erreurs sont rencontrées lors de la synchronisation.<br /><br /> **0** = compensation actions sont désactivées.<br /><br /> **1** = les modifications qui ne peut pas être appliquées à un abonné ou un serveur de publication entraînent toujours des actions de compensation pour annuler ces modifications, ce qui est le comportement par défaut pour la réplication de fusion.<br /><br /> Remarque : Une valeur de **0** entraîne une non-convergence.|  
|**pub_range**|**bigint**|Taille de la plage d'identité du serveur de publication.|  
|**range**|**bigint**|Taille des valeurs d'identité consécutives qui seraient affectées aux abonnés dans le cas d'un ajustement.|  
|**seuil**|**Int**|Seuil de la plage d'identité exprimé en pourcentage.|  
|**stream_blob_columns**|**bit**|Spécifie si une optimisation de flux de données est utilisée lors de la réplication de colonnes d'objets binaires volumineux. **1** signifie que l’optimisation est tentée.|  
|**preserve_rowguidcol**|**bit**|Indique si la réplication utilise une colonne rowguid existante. La valeur **1** signifie qu’une colonne ROWGUIDCOL existante est utilisée. **0** signifie que la réplication a ajouté la colonne ROWGUIDCOL.|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sp_addmergearticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md)   
 [sp_changemergearticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md)   
 [sp_helpmergearticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql.md)  
  
  
