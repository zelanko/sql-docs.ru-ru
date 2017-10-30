---
title: "Хранимые процедуры (каталог служб Integration Services) | Документы Microsoft"
ms.custom: 
ms.date: 12/16/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- stored procedures [Integration Services]
ms.assetid: a6ccd884-108f-4fb6-95ad-00b9cb65d5d6
caps.latest.revision: 19
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 21715bf65f3a85669dfe823511ddb9b6c2dd4d57
ms.contentlocale: ru-ru
ms.lasthandoff: 09/26/2017

---
# <a name="stored-procedures-integration-services-catalog"></a>Хранимые процедуры (каталог служб Integration Services)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  В этом разделе описываются хранимые процедуры [!INCLUDE[tsql](../../includes/tsql-md.md)], доступные для администрирования проектов служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], развернутых в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Вызовите [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] хранимые процедуры для добавления, удаления, изменения или выполнения объектов, которые хранятся в **SSISDB** каталога.  
  
 Имя каталога по умолчанию — SSISDB. Объекты, которые хранятся в каталоге, включают проекты, пакеты, параметры, среды и журнал операций.  
  
 Представления базы данных и хранимые процедуры можно использовать непосредственно или писать пользовательский код, который вызывает управляемый API. Среда [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] и управляемый API запрашивают представления и вызывают хранимые процедуры, описанные в этом разделе, для выполнения многих своих задач.  
  
## <a name="in-this-section"></a>В этом разделе  
 [catalog.add_data_tap](../../integration-services/system-stored-procedures/catalog-add-data-tap.md)  
 Добавляет отвод данных на выходе компонента в потоке данных пакета.  
  
 [catalog.add_data_tap_by_guid](../../integration-services/system-stored-procedures/catalog-add-data-tap-by-guid.md)  
 Добавляет отвод данных к определенному пути потока данных в потоке данных пакета.  
  
 [catalog.check_schema_version](../../integration-services/system-stored-procedures/catalog-check-schema-version.md)  
 Определяет, совместимы ли схема каталога SSISDB и двоичные файлы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] (сборка ISServerExec и SQLCLR).  
  
 [Catalog.clear_object_parameter_value &#40; База данных SSISDB &#41;](../../integration-services/system-stored-procedures/catalog-clear-object-parameter-value-ssisdb-database.md)  
 Очищает значение параметра для существующего проекта или пакета служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], который хранится на сервере.  
  
 [Catalog.configure_catalog &#40; База данных SSISDB &#41;](../../integration-services/system-stored-procedures/catalog-configure-catalog-ssisdb-database.md)  
 Настраивает каталог служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], задавая свойство каталога равным указанному значению.  
  
 [catalog.create_environment (база данных SSISDB)](../../integration-services/system-stored-procedures/catalog-create-environment-ssisdb-database.md)  
 Создает среду в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [catalog.create_environment_reference (база данных SSISDB)](../../integration-services/system-stored-procedures/catalog-create-environment-reference-ssisdb-database.md)  
 Создает ссылку на среду для проекта в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [catalog.create_environment_variable (база данных SSISDB)](../../integration-services/system-stored-procedures/catalog-create-environment-variable-ssisdb-database.md)  
 Создайте переменную среды в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [Catalog.create_execution &#40; База данных SSISDB &#41;](../../integration-services/system-stored-procedures/catalog-create-execution-ssisdb-database.md)  
 Создает экземпляр выполнения в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [catalog.create_execution_dump](../../integration-services/system-stored-procedures/catalog-create-execution-dump.md)  
 Приводит к приостановке выполняемого пакета и создает файл дампа.  
  
 [catalog.create_folder (база данных SSISDB)](../../integration-services/system-stored-procedures/catalog-create-folder-ssisdb-database.md)  
 Создает папку в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [catalog.delete_environment (база данных SSISDB)](../../integration-services/system-stored-procedures/catalog-delete-environment-ssisdb-database.md)  
 Удаляет среду из папки в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [catalog.delete_environment_reference (база данных SSISDB)](../../integration-services/system-stored-procedures/catalog-delete-environment-reference-ssisdb-database.md)  
 Удаляет ссылку на среду из проекта в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [catalog.delete_environment_variable (база данных SSISDB)](../../integration-services/system-stored-procedures/catalog-delete-environment-variable-ssisdb-database.md)  
 Удаляет переменную среды из среды в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [catalog.delete_folder (база данных SSISDB)](../../integration-services/system-stored-procedures/catalog-delete-folder-ssisdb-database.md)  
 Удаляет папку из каталога служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [catalog.delete_project (база данных SSISDB)](../../integration-services/system-stored-procedures/catalog-delete-project-ssisdb-database.md)  
 Удаляет существующий проект из папки в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [Catalog.deny_permission &#40; База данных SSISDB &#41;](../../integration-services/system-stored-procedures/catalog-deny-permission-ssisdb-database.md)  
 Отменяет разрешение на защищаемый объект в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [catalog.deploy_project (база данных SSISDB)](../../integration-services/system-stored-procedures/catalog-deploy-project-ssisdb-database.md)  
 Развертывает проект в папке каталога служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] или обновляет существующий проект, который был развернут ранее.  
  
 [Catalog.get_parameter_values &#40; База данных SSISDB &#41;](../../integration-services/system-stored-procedures/catalog-get-parameter-values-ssisdb-database.md)  
 Обеспечивает разрешение и выборку значений параметров по умолчанию из проекта и соответствующих пакетов в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [catalog.get_project (база данных SSISDB)](../../integration-services/system-stored-procedures/catalog-get-project-ssisdb-database.md)  
 Получает свойства существующего проекта в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [Catalog.grant_permission &#40; База данных SSISDB &#41;](../../integration-services/system-stored-procedures/catalog-grant-permission-ssisdb-database.md)  
 Предоставляет разрешение на защищаемый объект в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [catalog.move_environment (база данных SSISDB)](../../integration-services/system-stored-procedures/catalog-move-environment-ssisdb-database.md)  
 Перемещает среду из одной папки в другую в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [catalog.move_project (база данных SSISDB)](../Topic/catalog.move_project%20\(\(SSISDB%20Database\).md)  
 Перемещает проект из одной папки в другую в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [catalog.remove_data_tap](../../integration-services/system-stored-procedures/catalog-remove-data-tap.md)  
 Удаляет отвод данных с выхода компонента, находящегося в выполнении.  
  
 [catalog.rename_environment (база данных SSISDB)](../../integration-services/system-stored-procedures/catalog-rename-environment-ssisdb-database.md)  
 Переименовывает среду в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [catalog.rename_folder (база данных SSISDB)](../../integration-services/system-stored-procedures/catalog-rename-folder-ssisdb-database.md)  
 Переименовывает папку в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [catalog.restore_project (база данных SSISDB)](../../integration-services/system-stored-procedures/catalog-restore-project-ssisdb-database.md)  
 Восстанавливает проект в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] с переходом к предыдущей версии.  
  
 [Catalog.revoke_permission &#40; База данных SSISDB &#41;](../../integration-services/system-stored-procedures/catalog-revoke-permission-ssisdb-database.md)  
 Отзывает разрешение на защищаемый объект в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [catalog.set_environment_property (база данных SSISDB)](../../integration-services/system-stored-procedures/catalog-set-environment-property-ssisdb-database.md)  
 Задает свойство среды в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [catalog.set_environment_reference_type (база данных SSISDB)](../../integration-services/system-stored-procedures/catalog-set-environment-reference-type-ssisdb-database.md)  
 Задает ссылочный тип и имя среды, связанные с существующей ссылкой на среду для проекта в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [catalog.set_environment_variable_property (база данных SSISDB)](../../integration-services/system-stored-procedures/catalog-set-environment-variable-property-ssisdb-database.md)  
 Задает свойство переменной среды в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [Catalog.set_environment_variable_protection &#40; База данных SSISDB &#41;](../../integration-services/system-stored-procedures/catalog-set-environment-variable-protection-ssisdb-database.md)  
 Задает бит конфиденциальности переменной среды в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [catalog.set_environment_variable_value (база данных SSISDB)](../../integration-services/system-stored-procedures/catalog-set-environment-variable-value-ssisdb-database.md)  
 Задает значение переменной среды в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [catalog.set_execution_parameter_value (база данных SSISDB)](../../integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database.md)  
 Задает значение параметра для экземпляра выполнения в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [catalog.set_execution_property_override_value](../../integration-services/system-stored-procedures/catalog-set-execution-property-override-value.md)  
 Задает значение свойства для экземпляра выполнения в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [catalog.set_folder_description (база данных SSISDB)](../../integration-services/system-stored-procedures/catalog-set-folder-description-ssisdb-database.md)  
 Задает описание папки в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [Catalog.set_object_parameter_value &#40; База данных SSISDB &#41;](../../integration-services/system-stored-procedures/catalog-set-object-parameter-value-ssisdb-database.md)  
 Задает значение параметра в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Связывает значение с переменной среды или назначает литеральное значение, которое будет использоваться по умолчанию, если не будет назначено других значений.  
  
 [Catalog.start_execution &#40; База данных SSISDB &#41;](../../integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database.md)  
 Запускает экземпляр выполнения в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [catalog.startup](../../integration-services/system-stored-procedures/catalog-startup.md)  
 Осуществляет обслуживание состояния операций для каталога SSISDB.  
  
 [Catalog.stop_operation &#40; База данных SSISDB &#41;](../../integration-services/system-stored-procedures/catalog-stop-operation-ssisdb-database.md)  
 Останавливает проверку или экземпляр выполнения в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [Catalog.validate_package &#40; База данных SSISDB &#41;](../../integration-services/system-stored-procedures/catalog-validate-package-ssisdb-database.md)  
 Асинхронно проверяет пакет в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [Catalog.validate_project &#40; База данных SSISDB &#41;](../../integration-services/system-stored-procedures/catalog-validate-project-ssisdb-database.md)  
 Асинхронно проверяет проект в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
[Catalog.add_execution_worker &#40; База данных SSISDB &#41;](../../integration-services/system-stored-procedures/catalog-add-execution-worker-ssisdb-database.md)   
Добавляет [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] шкалы ожидания рабочий процесс, для экземпляра выполнения в масштабное развертывание.

[Catalog.enable_worker_agent &#40; База данных SSISDB &#41;](../../integration-services/system-stored-procedures/catalog-enable-worker-agent-ssisdb-database.md)   
Включить шкалы ожидания рабочий процесс для масштабирования ожидания базы данных Master работу с этим [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] каталога.

[Catalog.disable_worker_agent &#40; База данных SSISDB &#41;](../../integration-services/system-stored-procedures/catalog-disable-worker-agent-ssisdb-database.md)   
Отключить работника Out масштабирования для масштабирования Out Master работу с этим [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] каталога.



