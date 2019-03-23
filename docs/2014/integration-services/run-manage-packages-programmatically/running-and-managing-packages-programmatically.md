---
title: Выполнение пакетов и управление пакетами программным образом | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
ms.assetid: 1a08c75e-ce8c-45ee-81bd-32248bbdb2b2
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: ecbaa54a723fae6a3c5fd11363bf42f1f2a57da0
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2019
ms.locfileid: "58376473"
---
# <a name="running-and-managing-packages-programmatically"></a>Выполнение пакетов и управление пакетами программным образом
  Если требуется управлять пакетами служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] и выполнять их за пределами среды разработки, можно делать это программно. Этот подход предоставляет следующие возможности.  
  
-   Загрузка и выполнение существующего пакета без изменения.  
  
-   Загрузка существующего пакета, изменение его конфигурации (например, для другого источника данных) и выполнение пакета.  
  
-   Создание нового пакета, добавление и настройка компонентов поочередно для каждого объекта и для каждого свойства, сохранение пакета и выполнение пакета.  
  
 Можно загрузить и выполнить существующий пакет из клиентского приложения при помощи всего нескольких строк кода.  
  
 В этом разделе рассматривается программное выполнение существующего пакета и получение доступа к выходу потока данных из другого приложения. Дополнительной возможностью программирования является возможность программно создавать пакет служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] построчно, как описано в разделе [Программное построение пакетов](../building-packages-programmatically/building-packages-programmatically.md).  
  
 Также в этом разделе описываются другие задачи администрирования, которые можно выполнять программно для управления сохраненными пакетами, запуска пакетов и ролей пакетов.  
  
## <a name="running-packages-on-the-integration-services-server"></a>Выполнение пакетов на сервере службы Integration Services  
 При развертывании пакетов на сервере [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] можно запустить пакеты программным путем с помощью пространства имен <xref:Microsoft.SqlServer.Management.IntegrationServices>. Сборка Microsoft.SqlServer.Management.IntegrationServices компилируется с платформой .NET Framework 3.5. При построении приложения .NET Framework 4.0 может потребоваться добавить ссылку на сборку непосредственно в файл проекта.  
  
 Можно также использовать пространство имен для развертывания проектов [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] на сервере [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] и управления ими. Общие сведения о пространстве имен и фрагменты кода см. в записи блога [Обзор модели управляющих объектов каталога служб SSIS](https://go.microsoft.com/fwlink/?LinkId=253122) на сайте blogs.msdn.com.  
  
## <a name="in-this-section"></a>в этом разделе  
 [Основные сведения об отличиях между локальным и удаленным выполнением](../run-manage-packages-programmatically/understanding-the-differences-between-local-and-remote-execution.md)  
 Описываются важные различия между выполнением пакета локально и на сервере.  
  
 [Программная загрузка и запуск локального пакета](../run-manage-packages-programmatically/loading-and-running-a-local-package-programmatically.md)  
 Описывается процесс выполнения существующего пакета из клиентского приложения на локальном компьютере.  
  
 [Программная загрузка и запуск удаленного пакета](../run-manage-packages-programmatically/loading-and-running-a-remote-package-programmatically.md)  
 Описывается способ выполнения существующего пакета из клиентского приложения и способ убедиться, что пакет запущен на сервере.  
  
 [Загрузка выхода локального пакета](../run-manage-packages-programmatically/loading-the-output-of-a-local-package.md)  
 Описывается способ выполнения пакета на локальном компьютере и загрузки выходного потока данных в клиентское приложение с помощью назначения DataReader и пространства имен DtsClient.  
  
 [Программное перечисление доступных пакетов](../run-manage-packages-programmatically/enumerating-available-packages-programmatically.md)  
 Описывается способ обнаружения доступных пакетов, управляемых службами [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [Программное управление пакетами и папками](../run-manage-packages-programmatically/managing-packages-and-folders-programmatically.md)  
 Описывается создание, переименование и удаление как пакетов, так и папок.  
  
 [Программное управление запуском пакетов](../run-manage-packages-programmatically/managing-running-packages-programmatically.md)  
 Описывается создание списка запущенных в настоящее время пакетов, исследование их свойств и остановка пакетов.  
  
 [Программное управление ролями пакетов (служба SSIS)](../run-manage-packages-programmatically/managing-package-roles-programmatically-ssis-service.md)  
 Описывается получение или задание информации о ролях, назначенных пакету или папке.  
  
## <a name="reference"></a>Ссылка  
 [Справочник по сообщениям об ошибках служб Integration Services](../integration-services-error-and-message-reference.md)  
 Содержится список стандартных кодов ошибок служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] с символическими именами и описаниями.  
  
## <a name="related-sections"></a>См. также  
 [Расширение пакетов с помощью сценариев](../extending-packages-scripting/extending-packages-with-scripting.md)  
 Описываются вопросы расширения потока управления с помощью задачи «Скрипт» и расширения потока данных с помощью компонента скрипта.  
  
 [Расширение пакетов с помощью пользовательских объектов](../extending-packages-custom-objects/extending-packages-with-custom-objects.md)  
 Описываются вопросы программирования пользовательских задач, компонентов потока данных и других объектов пакета, используемых в нескольких пакетах.  
  
 [Программное построение пакетов](../building-packages-programmatically/building-packages-programmatically.md)  
 Описывается создание, настройка и сохранение пакетов служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] программным способом.  
  
![Значок служб Integration Services (маленький)](../media/dts-16.gif "значок служб Integration Services (маленький)")**оставаться до даты со службами Integration Services**<br /> Чтобы загрузить новейшую документацию, статьи, образцы и видеоматериалы [!INCLUDE[msCoName](../../includes/msconame-md.md)], а также лучшие решения участников сообщества, посетите страницу служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] на сайте MSDN:<br /><br /> [Посетите страницу служб Integration Services на сайте MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Чтобы получать автоматические уведомления об этих обновлениях, подпишитесь на RSS-каналы, предлагаемые на этой странице.  
  
## <a name="see-also"></a>См. также  
 [службы SQL Server Integration Services](../sql-server-integration-services.md)  
  
  
