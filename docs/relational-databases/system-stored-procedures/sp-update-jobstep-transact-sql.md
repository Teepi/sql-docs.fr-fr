---
title: sp_update_jobstep (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_update_jobstep
- sp_update_jobstep_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_update_jobstep
ms.assetid: e158802c-c347-4a5d-bf75-c03e5ae56e6b
caps.latest.revision: 33
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 43dfe2a04a6c4f12fad0df12c3cf520d7d08d7a7
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2018
ms.locfileid: "40392790"
---
# <a name="spupdatejobstep-transact-sql"></a>sp_update_jobstep (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Modifie la valeur d'une étape d'un travail qui est utilisé pour effectuer des activités automatisées.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_update_jobstep   
     {   [@job_id =] job_id   
       | [@job_name =] 'job_name' } ,  
     [@step_id =] step_id  
     [ , [@step_name =] 'step_name' ]  
     [ , [@subsystem =] 'subsystem' ]   
     [ , [@command =] 'command' ]  
     [ , [@additional_parameters =] 'parameters' ]  
     [ , [@cmdexec_success_code =] success_code ]  
     [ , [@on_success_action =] success_action ]   
     [ , [@on_success_step_id =] success_step_id ]  
     [ , [@on_fail_action =] fail_action ]   
     [ , [@on_fail_step_id =] fail_step_id ]  
     [ , [@server =] 'server' ]   
     [ , [@database_name =] 'database' ]  
     [ , [@database_user_name =] 'user' ]   
     [ , [@retry_attempts =] retry_attempts ]  
     [ , [@retry_interval =] retry_interval ]   
     [ , [@os_run_priority =] run_priority ]  
     [ , [@output_file_name =] 'file_name' ]   
     [ , [@flags =] flags ]  
     [ ,  {   [ @proxy_id = ] proxy_id   
            | [ @proxy_name = ] 'proxy_name' }   
```  
  
## <a name="arguments"></a>Arguments  
 [  **@job_id =**] *job_id*  
 Numéro d'identification du travail auquel l'étape appartient. *job_id*est **uniqueidentifier**, avec NULL comme valeur par défaut. Soit *job_id* ou *nom_travail* doit être spécifié, mais ne peut pas être spécifiés.  
  
 [  **@job_name =**] **'***nom_travail***'**  
 Nom du travail auquel l'étape appartient. *job_name*est **sysname**, avec NULL comme valeur par défaut. Soit *job_id* ou *nom_travail* doit être spécifié, mais ne peut pas être spécifiés.  
  
 [ **@step_id =**] *step_id*  
 Numéro d'identification de l'étape d'un travail à modifier. Il est impossible de modifier ce numéro. *l’argument id_étape*est **int**, sans valeur par défaut.  
  
 [  **@step_name =**] **'***nom_de_l***'**  
 Nouveau nom de l'étape. *nom_de_l*est **sysname**, avec NULL comme valeur par défaut.  
  
 [  **@subsystem =**] **'***sous-système***'**  
 Le sous-système utilisé par Microsoft SQL Server Agent pour exécuter *commande*. *sous-système* est **nvarchar (40)**, avec NULL comme valeur par défaut.  
  
 [  **@command =**] **'***commande***'**  
 L’exécution des commandes à exécuter via *sous-système*. *commande* est **nvarchar (max)**, avec NULL comme valeur par défaut.  
  
 [  **@additional_parameters =**] **'***paramètres***'**  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
 [  **@cmdexec_success_code =**] *code_succès*  
 La valeur retournée par un **CmdExec** commande du sous-système pour indiquer que *commande* exécutée avec succès. *code_succès* est **int**, avec NULL comme valeur par défaut.  
  
 [ **@on_success_action =**] *success_action*  
 L’action à effectuer si l’étape réussit. *action_succès* est **tinyint**, avec NULL comme valeur par défaut et peut prendre l’une des valeurs suivantes.  
  
|Valeur|Description (action)|  
|-----------|----------------------------|  
|**1**|Quitter avec succès.|  
|**2**|Sortie avec échec|  
|**3**|Passage à l'étape suivante|  
|**4**|Passez à l’étape *id_étape_succès.*|  
  
 [ **@on_success_step_id =**] *success_step_id*  
 Le numéro d’identification de l’étape du travail à exécuter si l’étape réussit et *action_succès* est **4**. *id_étape_succès* est **int**, avec NULL comme valeur par défaut.  
  
 [  **@on_fail_action =**] *action_échec*  
 L’action à effectuer si l’étape échoue. *action_échec* est **tinyint**, avec NULL comme valeur par défaut et peut avoir une des valeurs suivantes.  
  
|Valeur|Description (action)|  
|-----------|----------------------------|  
|**1**|Quitter avec succès.|  
|**2**|Sortie avec échec|  
|**3**|Passage à l'étape suivante|  
|**4**|Passez à l’étape *id_étape_échec **.*|  
  
 [  **@on_fail_step_id =**] *id_étape_échec*  
 Le numéro d’identification de l’étape du travail à exécuter si l’étape échoue et *action_échec* est **4**. *id_étape_échec* est **int**, avec NULL comme valeur par défaut.  
  
 [  **@server =**] **'***server***»**  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)] *serveur* est **nvarchar (128)**, avec NULL comme valeur par défaut.  
  
 [  **@database_name =**] **'***base de données***'**  
 Nom de la base de données dans laquelle l'étape [!INCLUDE[tsql](../../includes/tsql-md.md)] doit être exécutée. *base de données*est **sysname**. Les noms placés entre crochets ([ ]) ne sont pas autorisés. La valeur par défaut est NULL.  
  
 [  **@database_user_name =**] **'***utilisateur***'**  
 Nom du compte d'utilisateur à utiliser lors de l'exécution d'une étape [!INCLUDE[tsql](../../includes/tsql-md.md)]. *utilisateur*est **sysname**, avec NULL comme valeur par défaut.  
  
 [ **@retry_attempts =**] *retry_attempts*  
 Nombre de tentatives à effectuer si l'étape échoue. *retry_attempts*est **int**, avec NULL comme valeur par défaut.  
  
 [ **@retry_interval =**] *retry_interval*  
 Nombre de minutes s'écoulant entre chaque tentative de reprise. *intervalle_entre_reprises* est **int**, avec NULL comme valeur par défaut.  
  
 [  **@os_run_priority =**] *priorité_exécution*  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
 [  **@output_file_name =**] **'***file_name***'**  
 Nom du fichier dans lequel est enregistré le résultat de l'étape. *file_name* est **nvarchar (200)**, avec NULL comme valeur par défaut. Ce paramètre est valide uniquement avec les commandes fonctionnant dans les sous-systèmes [!INCLUDE[tsql](../../includes/tsql-md.md)] ou CmdExec.  
  
 Pour définir nom_fichier_sortie NULL, vous devez définir *nom_fichier_sortie* sur une chaîne vide (' ') ou à une chaîne de caractères vides, mais vous ne pouvez pas utiliser le **CHAR(32)** (fonction). Vous pouvez par exemple définir cet argument avec une chaîne vide comme suit :  
  
 **@output_file_name = ' '**  
  
 [  **@flags =**] *indicateurs*  
 Une option qui contrôle le comportement. *indicateurs* est **int**, et peut prendre l’une des valeurs suivantes.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**0** (valeur par défaut)|Écrasement du fichier de sortie.|  
|**2**|Ajout au fichier de sortie|  
|**4**|Écriture de la sortie de l'étape d'un travail Transact-SQL dans l'historique des étapes.|  
|**8**|Écriture du journal dans la table (remplace l'historique existant)|  
|**16**|Écriture du journal dans la table (s'ajoute à l'historique existant)|  
  
 [ **@proxy_id**=] *proxy_id*  
 Numéro d'identification du proxy sous lequel s'exécute l'étape de travail. *proxy_id* est de type **int**, avec NULL comme valeur par défaut. Si aucun *proxy_id* est spécifié, aucun *proxy_name* est spécifié et aucune *user_name* est spécifié, l’étape de travail s’exécute en tant que compte de service pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.  
  
 [ **@proxy_name**=] **'***proxy_name***'**  
 Nom du proxy sous lequel s'exécute l'étape de travail. *proxy_name* est de type **sysname**, avec NULL comme valeur par défaut. Si aucun *proxy_id* est spécifié, aucun *proxy_name* est spécifié et aucune *user_name* est spécifié, l’étape de travail s’exécute en tant que compte de service pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_update_jobstep** doit être exécuté à partir de la **msdb** base de données.  
  
 La mise à jour de l'étape d'un travail incrémente le numéro de version de ce travail.  
  
## <a name="permissions"></a>Permissions  
 Par défaut, les membres du rôle serveur fixe **sysadmin** peuvent exécuter cette procédure stockée. Les autres utilisateurs doivent disposer de l'un des rôles de base de données fixes suivants de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent dans la base de données **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Pour en savoir plus sur les autorisations de ces rôles, consultez [Rôles de base de données fixes de l'Agent SQL Server](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
 Seuls les membres du **sysadmin** mettre à jour une étape de travail appartienne à un autre utilisateur.  
  
 Si l'étape d'un travail nécessite un accès à un proxy, le créateur de l'étape doit avoir accès au proxy pour l'étape du travail. Tous les sous-systèmes, excepté Transact-SQL, requièrent un compte proxy. Membres de **sysadmin** ont accès à tous les serveurs proxy et pouvez utiliser le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] compte de service Agent pour le proxy.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant modifie le nombre de tentatives de reprises pour la première étape du travail `Weekly Sales Data Backup`. À la fin de l'exemple, ce nombre s'élève à `10`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_update_jobstep  
    @job_name = N'Weekly Sales Data Backup',  
    @step_id = 1,  
    @retry_attempts = 10 ;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Afficher ou modifier les travaux](../../ssms/agent/view-or-modify-jobs.md)   
 [sp_delete_jobstep &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-jobstep-transact-sql.md)   
 [sp_help_jobstep &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-jobstep-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
