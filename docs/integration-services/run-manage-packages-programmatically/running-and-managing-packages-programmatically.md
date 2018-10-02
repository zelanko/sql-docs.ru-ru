---
title: Выполнение пакетов и управление пакетами программным образом | Документы Майкрософт
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
ms.assetid: 1a08c75e-ce8c-45ee-81bd-32248bbdb2b2
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 1e6dee6bea3a3d4c0c6cd5c2f7bb3f6ac51abe88
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47656702"
---
# <a name="running-and-managing-packages-programmatically"></a>Выполнение пакетов и управление пакетами программным образом
  Если требуется управлять пакетами служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] и выполнять их за пределами среды разработки, можно делать это программно. Этот подход предоставляет следующие возможности.  
  
-   Загрузка и выполнение существующего пакета без изменения.  
  
-   Загрузка существующего пакета, изменение его конфигурации (например, для другого источника данных) и выполнение пакета.  
  
-   Создание нового пакета, добавление и настройка компонентов поочередно для каждого объекта и для каждого свойства, сохранение пакета и выполнение пакета.  
  
 Можно загрузить и выполнить существующий пакет из клиентского приложения при помощи всего нескольких строк кода.  
  
 В этом разделе рассматривается программное выполнение существующего пакета и получение доступа к выходу потока данных из другого приложения. Дополнительной возможностью программирования является возможность программно создавать пакет служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] построчно, как описано в разделе [Программное построение пакетов](../../integration-services/building-packages-programmatically/building-packages-programmatically.md).  
  
 Также в этом разделе описываются другие задачи администрирования, которые можно выполнять программно для управления сохраненными пакетами, запуска пакетов и ролей пакетов.  
  
## <a name="running-packages-on-the-integration-services-server"></a>Выполнение пакетов на сервере службы Integration Services  
 При развертывании пакетов на сервере [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] можно запустить пакеты программным путем с помощью пространства имен <xref:Microsoft.SqlServer.Management.IntegrationServices>. Сборка Microsoft.SqlServer.Management.IntegrationServices компилируется с платформой .NET Framework 3.5. При построении приложения .NET Framework 4.0 может потребоваться добавить ссылку на сборку непосредственно в файл проекта.  
  
 Можно также использовать пространство имен для развертывания проектов [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] на сервере [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] и управления ими. Общие сведения о пространстве имен и фрагменты кода см. в записи блога [Обзор модели управляющих объектов каталога служб SSIS](http://go.microsoft.com/fwlink/?LinkId=253122) на сайте blogs.msdn.com.  
  
## <a name="in-this-section"></a>в этом разделе  
 [Основные сведения об отличиях между локальным и удаленным выполнением](../../integration-services/run-manage-packages-programmatically/understanding-the-differences-between-local-and-remote-execution.md)  
 Описываются важные различия между выполнением пакета локально и на сервере.  
  
 [Программная загрузка и запуск локального пакета](../../integration-services/run-manage-packages-programmatically/loading-and-running-a-local-package-programmatically.md)  
 Описывается процесс выполнения существующего пакета из клиентского приложения на локальном компьютере.  
  
 [Программная загрузка и запуск удаленного пакета](../../integration-services/run-manage-packages-programmatically/loading-and-running-a-remote-package-programmatically.md)  
 Описывается способ выполнения существующего пакета из клиентского приложения и способ убедиться, что пакет запущен на сервере.  
  
 [Загрузка выхода локального пакета](../../integration-services/run-manage-packages-programmatically/loading-the-output-of-a-local-package.md)  
 Описывается способ выполнения пакета на локальном компьютере и загрузки выходного потока данных в клиентское приложение с помощью назначения DataReader и пространства имен DtsClient.  
  
 [Программное перечисление доступных пакетов](../../integration-services/run-manage-packages-programmatically/enumerating-available-packages-programmatically.md)  
 Описывается способ обнаружения доступных пакетов, управляемых службами [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [Программное управление пакетами и папками](../../integration-services/run-manage-packages-programmatically/managing-packages-and-folders-programmatically.md)  
 Описывается создание, переименование и удаление как пакетов, так и папок.  
  
 [Программное управление запуском пакетов](../../integration-services/run-manage-packages-programmatically/managing-running-packages-programmatically.md)  
 Описывается создание списка запущенных в настоящее время пакетов, исследование их свойств и остановка пакетов.  
  
 [Программное управление ролями пакетов (служба SSIS)](../../integration-services/run-manage-packages-programmatically/managing-package-roles-programmatically-ssis-service.md)  
 Описывается получение или задание информации о ролях, назначенных пакету или папке.  
  
## <a name="reference"></a>Справочник  
 [Справочник по сообщениям об ошибках служб Integration Services](../../integration-services/integration-services-error-and-message-reference.md)  
 Содержится список стандартных кодов ошибок служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] с символическими именами и описаниями.  
  
## <a name="related-sections"></a>См. также  
 [Расширение пакетов с помощью сценариев](../../integration-services/extending-packages-scripting/extending-packages-with-scripting.md)  
 Описываются вопросы расширения потока управления с помощью задачи «Скрипт» и расширения потока данных с помощью компонента скрипта.  
  
 [Расширение пакетов с помощью пользовательских объектов](../../integration-services/extending-packages-custom-objects/extending-packages-with-custom-objects.md)  
 Описываются вопросы программирования пользовательских задач, компонентов потока данных и других объектов пакета, используемых в нескольких пакетах.  
  
 [Программное построение пакетов](../../integration-services/building-packages-programmatically/building-packages-programmatically.md)  
 Описывается создание, настройка и сохранение пакетов служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] программным способом.  
  
## <a name="see-also"></a>См. также:  
 [службы SQL Server Integration Services](../../integration-services/sql-server-integration-services.md)  
  
  
