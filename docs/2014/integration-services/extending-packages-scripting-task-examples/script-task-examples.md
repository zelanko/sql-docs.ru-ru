---
title: Примеры задачи "Скрипт" | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Script task [Integration Services], examples
- examples [Integration Services]
- SSIS Script task, examples
ms.assetid: b0dd77ee-ee11-4cd9-87aa-61dd67f2fe1c
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: d47fa22b8207facc5b4bc22a4077b8bd81837ec2
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62768482"
---
# <a name="script-task-examples"></a>Примеры задачи «Скрипт»
  Задача «Скрипт» — это многоцелевой инструмент, который можно использовать в пакете для выполнения практически любых действий, которые невозможно произвести с помощью задач, поставляемых со службами [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. В этом разделе приведены образцы кода задачи «Скрипт», в которых демонстрируются некоторые элементы доступной функциональности.  
  
> [!NOTE]  
>  Если необходимо создать задачи, пригодные для повторного использования в нескольких пакетах, рассмотрите возможность использования кода в этих образцах как отправной точки для создания пользовательских задач. Дополнительные сведения см. в разделе [Разработка пользовательской задачи](../extending-packages-custom-objects/task/developing-a-custom-task.md).  
  
## <a name="in-this-section"></a>в этом разделе  
  
### <a name="example-topics"></a>Разделы с образцами  
 В этом разделе содержатся примеры кода, демонстрирующие различные варианты использования классов платформы [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], которые можно включить в задачу «Скрипт» служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [Обнаружение пустого неструктурированного файла в задаче «Скрипт»](../extending-packages-scripting-task-examples/detecting-an-empty-flat-file-with-the-script-task.md)  
 Проверяет неструктурированный файл, чтобы определить, содержит ли он строки данных, и сохраняет результат в переменную для использования в ветвлении потока управления.  
  
 [Составление списка для цикла по каждому элементу в задаче «Скрипт»](../extending-packages-scripting-task-examples/gathering-a-list-for-the-foreach-loop-with-the-script-task.md)  
 Собирает список файлов, отвечающих заданным пользователем критериям, и заполняет переменную для использования в дальнейшем в перечислителе по объекту из переменной.  
  
 [Запрос Active Directory в задаче «Скрипт»](../extending-packages-scripting-task-examples/querying-the-active-directory-with-the-script-task.md)  
 Извлекает сведения о пользователе из службы каталогов Active Directory на основе значения переменной служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] с использованием классов в пространстве имен System.DirectoryServices.  
  
 [Наблюдение за счетчиками производительности в задаче «Скрипт»](../extending-packages-scripting-task-examples/monitoring-performance-counters-with-the-script-task.md)  
 Создает пользовательский счетчик производительности, который можно использовать для отслеживания хода выполнения пакета служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], применяя классы в пространстве имен System.Diagnostics.  
  
 [Работа с изображениями в задаче «Скрипт»](../extending-packages-scripting-task-examples/working-with-images-with-the-script-task.md)  
 Выполняет сжатие изображений в формат JPEG и создает из них эскизы изображений, используя классы в пространстве имен System.Drawing.  
  
 [Обнаружение установленных принтеров с помощью задачи «Скрипт»](../extending-packages-scripting-task-examples/finding-installed-printers-with-the-script-task.md)  
 Осуществляет поиск установленных принтеров, поддерживающих определенный размер бумаги, используя классы в пространстве имен System.Drawing.Printing.  
  
 [Отправка почтового сообщения в формате HTML с помощью задачи «Скрипт»](../extending-packages-scripting-task-examples/sending-an-html-mail-message-with-the-script-task.md)  
 Отправляет почтовое сообщение в формате HTML вместо обычного текстового формата.  
  
 [Работа с файлами Excel в задаче «Скрипт»](../extending-packages-scripting-task-examples/working-with-excel-files-with-the-script-task.md)  
 Создает список листов в файле Excel и проверяет существование определенного листа.  
  
 [Отправка в удаленную закрытую очередь сообщений в задаче «Скрипт»](../extending-packages-scripting-task-examples/sending-to-a-remote-private-message-queue-with-the-script-task.md)  
 Отправляет сообщение в удаленную закрытую очередь сообщений.  
  
### <a name="other-examples"></a>Другие образцы  
 В разделах, перечисленных ниже, также содержатся примеры кода для использования с задачей «Скрипт».  
  
 [Использование переменных в задаче «Скрипт»](../extending-packages-scripting/task/using-variables-in-the-script-task.md)  
 Запрашивает у пользователя подтверждение продолжения работы пакета на основе значения переменной пакета, которое может превысить предел, указанный в другой переменной.  
  
 [Соединение с источниками данных в задаче «Скрипт»](../extending-packages-scripting/task/connecting-to-data-sources-in-the-script-task.md)  
 Извлекает соединение или данные соединения из диспетчеров соединений, определенных в пакете.  
  
 [Вызов событий в задаче «Скрипт»](../extending-packages-scripting/task/raising-events-in-the-script-task.md)  
 Выдает ошибку, предупреждение или информационное сообщение в зависимости от состояния соединения с Интернетом на сервере.  
  
 [Ведение журнала в задаче «Скрипт»](../extending-packages-scripting/task/logging-in-the-script-task.md)  
 Регистрирует число элементов, обработанных задачей в активных регистраторах.  
  
![Значок служб Integration Services (маленький)](../media/dts-16.gif "значок служб Integration Services (маленький)")**оставаться до даты со службами Integration Services**<br /> Чтобы загрузить новейшую документацию, статьи, образцы и видеоматериалы корпорации Майкрософт, а также лучшие решения участников сообщества, посетите страницу служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] на сайте MSDN:<br /><br /> [Посетите страницу служб Integration Services на сайте MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Чтобы получать автоматические уведомления об этих обновлениях, подпишитесь на RSS-каналы, предлагаемые на этой странице.  
  
  
