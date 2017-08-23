---
title: "К категории операции веб-службы (Master Data Services) | Документы Microsoft"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: e3f346b5-7e26-481d-9821-1846e2e91289
caps.latest.revision: 7
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 5363c242248d57e23da9aae986f39825896d5162
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="categorized-web-service-operations-master-data-services"></a>Операции веб-службы по категориям (службы Master Data Services)
  Веб-служба [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] содержит полный набор операций, позволяющих писать код для управления всеми функциями веб-приложения [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] через его пользовательский интерфейс. Операции веб-службы определяются интерфейсом <xref:Microsoft.MasterDataServices.IService> и реализуются в виде методов класса <xref:Microsoft.MasterDataServices.ServiceClient>. В этом разделе операции веб-службы сгруппированы по основным категориям для того, чтобы было проще понять, как пользоваться API-интерфейсом веб-службы.  
  
## <a name="model-operations"></a>Операции с моделью  
 С помощью этих операций выполняется создание, обновление или удаление моделей, а также управление всем содержимым модели, например сущностями, иерархиями и версиями. Дополнительные сведения см. в разделе [Модели (службы Master Data Services)](../../master-data-services/models-master-data-services.md).  
  
||  
|-|  
|<xref:Microsoft.MasterDataServices.ServiceClient.MetadataClone%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.MetadataCreate%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.MetadataDelete%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.MetadataGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.MetadataUpdate%2A>|  
  
## <a name="entity-operations"></a>Операции с сущностями  
 Эти операции служат для создания, обновления и удаления элементов одной сущности. Дополнительные сведения см. в разделе [сущности &#40; Службы Master Data Services &#41; ](../../master-data-services/entities-master-data-services.md) и [члены &#40; Службы Master Data Services &#41; ](../../master-data-services/members-master-data-services.md).  
  
||  
|-|  
|<xref:Microsoft.MasterDataServices.ServiceClient.EntityMemberKeyLookup%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.EntityMembersCopy%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.EntityMembersCreate%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.EntityMembersDelete%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.EntityMembersGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.EntityMembersMerge%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.EntityMembersUpdate%2A>|  
  
## <a name="member-operations"></a>Операции с элементами  
 Эти операции служат для получения, обновления и удаления элементов. Набор элементов, с которыми выполняется операция, может содержать элементы из нескольких сущностей. Дополнительные сведения см. в разделе [Элементы (службы Master Data Services)](../../master-data-services/members-master-data-services.md).  
  
||  
|-|  
|<xref:Microsoft.MasterDataServices.ServiceClient.ModelMembersBulkDelete%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.ModelMembersBulkMerge%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.ModelMembersBulkUpdate%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.ModelMembersGet%2A>|  
  
## <a name="attribute-and-hierarchy-operations"></a>Операции с атрибутами и иерархиями  
 Эти операции служат для получения сведений об атрибутах и иерархиях. Атрибуты и иерархии также можно изменять с помощью операций с моделями, например <xref:Microsoft.MasterDataServices.ServiceClient.MetadataUpdate%2A>. Дополнительные сведения см. в разделе [атрибуты &#40; Службы Master Data Services &#41; ](../../master-data-services/attributes-master-data-services.md) и [иерархий &#40; Службы Master Data Services &#41; ](../../master-data-services/hierarchies-master-data-services.md).  
  
||  
|-|  
|<xref:Microsoft.MasterDataServices.ServiceClient.EntityMemberAttributesGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.HierarchyMembersGet%2A>|  
  
## <a name="business-rule-operations"></a>Операции с бизнес-правилами  
 Эти операции используются для создания, обновления, удаления и публикации бизнес-правил. Дополнительные сведения см. в статье [Бизнес-правила (службы Master Data Services)](../../master-data-services/business-rules-master-data-services.md).  
  
||  
|-|  
|<xref:Microsoft.MasterDataServices.ServiceClient.BusinessRulesClone%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.BusinessRulesCreate%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.BusinessRulesDelete%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.BusinessRulesGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.BusinessRulesPaletteGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.BusinessRulesPublish%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.BusinessRulesUpdate%2A>|  
  
## <a name="annotation-operations"></a>Операции с заметками  
 Эти операции служат для создания, обновления и удаления заметок. Дополнительные сведения см. в разделе [заметки &#40; Службы Master Data Services &#41; ](../../master-data-services/annotations-master-data-services.md).  
  
||  
|-|  
|<xref:Microsoft.MasterDataServices.ServiceClient.AnnotationsDelete%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.AnnotationsUpdate%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.EntityMemberAnnotationsCreate%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.EntityMemberAnnotationsGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.TransactionAnnotationsCreate%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.TransactionAnnotationsGet%2A>|  
  
## <a name="transaction-operations"></a>Операции с транзакциями  
 Эти операции служат для получения и отмены транзакций. Дополнительные сведения см. в разделе [Транзакции (службы Master Data Services)](../../master-data-services/transactions-master-data-services.md).  
  
||  
|-|  
|<xref:Microsoft.MasterDataServices.ServiceClient.TransactionsGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.TransactionsReverse%2A>|  
  
## <a name="version-and-validation-operations"></a>Операции проверки и операции с версиями  
 Эти операции используются для копирования и проверки версий. Дополнительные сведения см. в разделе [версии &#40; Службы Master Data Services &#41; ](../../master-data-services/versions-master-data-services.md) и [проверку &#40; Службы Master Data Services &#41; ](../../master-data-services/validation-master-data-services.md).  
  
||  
|-|  
|<xref:Microsoft.MasterDataServices.ServiceClient.VersionCopy%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.ValidationGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.ValidationProcess%2A>|  
  
## <a name="data-quality-operations"></a>Операции по обеспечению качества данных  
 С помощью этих операций выполняются задачи по обеспечению качества данных, а также оценка результатов.  
  
||  
|-|  
|<xref:Microsoft.MasterDataServices.ServiceClient.DataQualityCleansingOperationCreate%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.DataQualityMatchingOperationCreate%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.DataQualityInstalledState%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.DataQualityKnowledgeBasesGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.DataQualityOperationStart%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.DataQualityOperationResultsGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.DataQualityOperationStatus%2A>|  
  
## <a name="data-import-operations"></a>Операции импорта данных  
 Эти операции используются для импорта данных в базу данных [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] . Дополнительные сведения см. в разделе [Обзор: импорт данных из таблиц (службы Master Data Services)](../../master-data-services/overview-importing-data-from-tables-master-data-services.md).  
  
||  
|-|  
|<xref:Microsoft.MasterDataServices.ServiceClient.EntityStagingClear%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.EntityStagingGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.EntityStagingLoad%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.EntityStagingProcess%2A>|  
  
 Следующие операции используются для импорта данных с помощью промежуточного процесса в [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]. Эти операции следует использовать только для поддержки существующих баз данных. Для новых разработок используйте приведенные ранее операции.  
  
||  
|-|  
|<xref:Microsoft.MasterDataServices.ServiceClient.StagingClear%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.StagingGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.StagingNameCheck%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.StagingProcess%2A>|  
  
## <a name="data-export-operations"></a>Операции экспорта данных  
 Эти операции используются для экспорта данных посредством использования представлений подписки. Дополнительные сведения см. в разделе [Overview: Exporting Data &#40;Master Data Services&#41;](../../master-data-services/overview-exporting-data-master-data-services.md).  
  
||  
|-|  
|<xref:Microsoft.MasterDataServices.ServiceClient.ExportViewCreate%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.ExportViewDelete%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.ExportViewListGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.ExportViewUpdate%2A>|  
  
## <a name="security-operations"></a>Операции по обеспечению безопасности  
 С помощью этих операций выполняется изменение параметров безопасности, управляющих доступом к базе данных [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] . Дополнительные сведения см. в разделе [Безопасность (службы Master Data Services)](../../master-data-services/security-master-data-services.md).  
  
||  
|-|  
|<xref:Microsoft.MasterDataServices.ServiceClient.SecurityPrincipalsClone%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.SecurityPrincipalsCreate%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.SecurityPrincipalsDelete%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.SecurityPrincipalsGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.SecurityPrincipalsUpdate%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.SecurityPrivilegesClone%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.SecurityPrivilegesCreate%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.SecurityPrivilegesDelete%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.SecurityPrivilegesGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.SecurityPrivilegesUpdate%2A>|  
  
## <a name="system-operations"></a>Системные операции  
 Эти операции используются для определения и обновления параметров системы и персональных настроек пользователя.  
  
||  
|-|  
|<xref:Microsoft.MasterDataServices.ServiceClient.ServiceCheck%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.ServiceVersionGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.SystemDomainListGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.SystemPropertiesGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.SystemSettingsGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.SystemSettingsUpdate%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.UserPreferencesDelete%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.UserPreferencesGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.UserPreferencesUpdate%2A>|  
  
  
