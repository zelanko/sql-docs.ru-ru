---
title: Представления (каталог служб Integration Services) | Документы Майкрософт
ms.custom: ''
ms.date: 12/16/2016
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
helpviewer_keywords:
- views [Integration Services]
ms.assetid: d0294d43-4852-46dc-9afa-d0c19ea9aa03
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 19b15e078e077a7a448ae95ddc9f4b9e14093e64
ms.sourcegitcommit: 7ccb8f28eafd79a1bddd523f71fe8b61c7634349
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2019
ms.locfileid: "58290550"
---
# <a name="views-integration-services-catalog"></a>Представления (каталог служб Integration Services)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  В этом разделе описываются отображения [!INCLUDE[tsql](../../includes/tsql-md.md)], доступные для администрирования проектов служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], развернутых в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Запросы к представлениям служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] позволяют просматривать объекты, параметры и рабочие данные, которые хранятся в каталоге **SSISDB**.  
  
 Имя каталога по умолчанию — SSISDB. Объекты, которые хранятся в каталоге, включают проекты, пакеты, параметры, среды и журнал операций.  
  
 Представления базы данных и хранимые процедуры можно использовать непосредственно или писать пользовательский код, который вызывает управляемый API. Среда [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] и управляемый API запрашивают представления и вызывают хранимые процедуры, описанные в этом разделе, для выполнения многих своих задач.  
  
## <a name="in-this-section"></a>в этом разделе  
 [catalog.catalog_properties (база данных SSISDB)](../../integration-services/system-views/catalog-catalog-properties-ssisdb-database.md)  
 Отображает свойства каталога служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [catalog.effective_object_permissions (база данных SSISDB)](../../integration-services/system-views/catalog-effective-object-permissions-ssisdb-database.md)  
 Отображает действующие разрешения текущего участника для всех объектов в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [catalog.environment_variables (база данных SSISDB)](../../integration-services/system-views/catalog-environment-variables-ssisdb-database.md)  
 Отображает подробные сведения о переменных среды для всех сред в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [catalog.environments (база данных SSISDB)](../../integration-services/system-views/catalog-environments-ssisdb-database.md)  
 Отображает подробные сведения о среде для всех сред в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Среды содержат переменные, на которые могут ссылаться проекты служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [catalog.execution_parameter_values (база данных SSISDB)](../../integration-services/system-views/catalog-execution-parameter-values-ssisdb-database.md)  
 Отображает фактические значения параметров, которые используются пакетами служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] на экземпляре выполнения.  
  
 [catalog.executions (база данных SSISDB)](../../integration-services/system-views/catalog-executions-ssisdb-database.md)  
 Отображает экземпляры выполнения пакета в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Пакеты, которые выполняются с помощью задачи «Выполнение пакета», запускаются в том же экземпляре выполнения, что и родительский пакет.  
  
 [catalog.explicit_object_permissions (база данных SSISDB)](../../integration-services/system-views/catalog-explicit-object-permissions-ssisdb-database.md)  
 Отображает только разрешения, которые были явно назначены пользователю.  
  
 [catalog.extended_operation_info (база данных SSISDB)](../../integration-services/system-views/catalog-extended-operation-info-ssisdb-database.md)  
 Отображает расширенные сведения для всех операций в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [catalog.folders (база данных SSISDB)](../../integration-services/system-views/catalog-folders-ssisdb-database.md)  
 Отображает папки в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [catalog.object_parameters (база данных SSISDB)](../../integration-services/system-views/catalog-object-parameters-ssisdb-database.md)  
 Отображает параметры для всех пакетов и проектов в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [catalog.object_versions (база данных SSISDB)](../../integration-services/system-views/catalog-object-versions-ssisdb-database.md)  
 Отображает версии объектов в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. В этом выпуске в данном представлении поддерживаются только версии проектов.  
  
 [catalog.operation_messages (база данных SSISDB)](../../integration-services/system-views/catalog-operation-messages-ssisdb-database.md)  
 Отображает сообщения, которые заносятся в журнал при выполнении операций в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [catalog.operations (база данных SSISDB)](../../integration-services/system-views/catalog-operations-ssisdb-database.md)  
 Отображает подробные сведения обо всех операциях в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [catalog.packages (база данных SSISDB)](../../integration-services/system-views/catalog-packages-ssisdb-database.md)  
 Отображает подробные сведения для всех пакетов, которые появляются в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [catalog.environment_references (база данных SSISDB)](../../integration-services/system-views/catalog-environment-references-ssisdb-database.md)  
 Отображает ссылки на среду для всех проектов в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [catalog.projects (база данных SSISDB)](../../integration-services/system-views/catalog-projects-ssisdb-database.md)  
 Отображает подробные сведения для всех проектов, которые находятся в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [catalog.validations (база данных SSISDB)](../../integration-services/system-views/catalog-validations-ssisdb-database.md)  
 Отображает сведения о проверке правильности всех проектов и пакетов в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
[catalog.master_properties (база данных SSISDB)](../../integration-services/system-views/catalog-master-properties-ssisdb-database.md)  
Отображает свойства мастера [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Scale Out.

[catalog.worker_agents (база данных SSISDB)](../../integration-services/system-views/catalog-worker-agents-ssisdb-database.md)  
Отображает сведения для рабочей роли [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Scale Out.  
