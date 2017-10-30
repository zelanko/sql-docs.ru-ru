---
title: "Примеры задач скрипта | Документы Microsoft"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
dev_langs:
- VB
helpviewer_keywords:
- Script task [Integration Services], examples
- examples [Integration Services]
- SSIS Script task, examples
ms.assetid: b0dd77ee-ee11-4cd9-87aa-61dd67f2fe1c
caps.latest.revision: 26
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: f7732abe880aa5eeaab2030da423e18d1977d64a
ms.contentlocale: ru-ru
ms.lasthandoff: 09/26/2017

---
# <a name="script-task-examples"></a>Примеры задачи «Скрипт»
  Задача «Скрипт» — это многоцелевой инструмент, который можно использовать в пакете для выполнения практически любых действий, которые невозможно произвести с помощью задач, поставляемых со службами [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. В этом разделе приведены образцы кода задачи «Скрипт», в которых демонстрируются некоторые элементы доступной функциональности.  
  
> [!NOTE]  
>  Если необходимо создать задачи, пригодные для повторного использования в нескольких пакетах, рассмотрите возможность использования кода в этих образцах как отправной точки для создания пользовательских задач. Дополнительные сведения см. в разделе [Разработка пользовательской задачи](../../integration-services/extending-packages-custom-objects/task/developing-a-custom-task.md).  
  
## <a name="in-this-section"></a>В этом разделе  
  
### <a name="example-topics"></a>Разделы с образцами  
 В этом разделе содержатся примеры кода, демонстрирующие различные варианты использования классов платформы [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], которые можно включить в задачу «Скрипт» служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [Обнаружение пустого неструктурированного файла в задаче «Скрипт»](../../integration-services/extending-packages-scripting-task-examples/detecting-an-empty-flat-file-with-the-script-task.md)  
 Проверяет неструктурированный файл, чтобы определить, содержит ли он строки данных, и сохраняет результат в переменную для использования в ветвлении потока управления.  
  
 [Составление списка для цикла по каждому элементу в задаче «Скрипт»](../../integration-services/extending-packages-scripting-task-examples/gathering-a-list-for-the-foreach-loop-with-the-script-task.md)  
 Собирает список файлов, отвечающих заданным пользователем критериям, и заполняет переменную для использования в дальнейшем в перечислителе по объекту из переменной.  
  
 [Запрос Active Directory в задаче «Скрипт»](../../integration-services/extending-packages-scripting-task-examples/querying-the-active-directory-with-the-script-task.md)  
 Извлекает сведения о пользователе из Active Directory на основе значения [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] переменной с помощью классов в пространстве имен System.DirectoryServices.  
  
 [Наблюдение за счетчиками производительности в задаче «Скрипт»](../../integration-services/extending-packages-scripting-task-examples/monitoring-performance-counters-with-the-script-task.md)  
 Создает пользовательский счетчик производительности, можно использовать для отслеживания хода выполнения [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] пакета с помощью классов в пространстве имен System.Diagnostics.  
  
 [Работа с изображениями в задаче «Скрипт»](../../integration-services/extending-packages-scripting-task-examples/working-with-images-with-the-script-task.md)  
 Выполняет сжатие изображений в формате JPEG и создает миниатюрные изображения их, используя классы в пространстве имен System.Drawing.  
  
 [Обнаружение установленных принтеров с помощью задачи «Скрипт»](../../integration-services/extending-packages-scripting-task-examples/finding-installed-printers-with-the-script-task.md)  
 Поиск установленных принтеров, поддерживающих определенный размер бумаги, используя классы в пространстве имен System.Drawing.Printing.  
  
 [Отправка почтового сообщения в формате HTML с помощью задачи «Скрипт»](../../integration-services/extending-packages-scripting-task-examples/sending-an-html-mail-message-with-the-script-task.md)  
 Отправляет почтовое сообщение в формате HTML вместо обычного текстового формата.  
  
 [Работа с файлами Excel в задаче «Скрипт»](../../integration-services/extending-packages-scripting-task-examples/working-with-excel-files-with-the-script-task.md)  
 Создает список листов в файле Excel и проверяет существование определенного листа.  
  
 [Отправка в удаленную закрытую очередь сообщений в задаче «Скрипт»](../../integration-services/extending-packages-scripting-task-examples/sending-to-a-remote-private-message-queue-with-the-script-task.md)  
 Отправляет сообщение в удаленную закрытую очередь сообщений.  
  
### <a name="other-examples"></a>Другие образцы  
 В разделах, перечисленных ниже, также содержатся примеры кода для использования с задачей «Скрипт».  
  
 [Использование переменных в задаче «Скрипт»](../../integration-services/extending-packages-scripting/task/using-variables-in-the-script-task.md)  
 Запрашивает у пользователя подтверждение продолжения работы пакета на основе значения переменной пакета, которое может превысить предел, указанный в другой переменной.  
  
 [Соединение с источниками данных в задаче «Скрипт»](../../integration-services/extending-packages-scripting/task/connecting-to-data-sources-in-the-script-task.md)  
 Извлекает соединение или данные соединения из диспетчеров соединений, определенных в пакете.  
  
 [Вызов событий в задаче «Скрипт»](../../integration-services/extending-packages-scripting/task/raising-events-in-the-script-task.md)  
 Выдает ошибку, предупреждение или информационное сообщение в зависимости от состояния соединения с Интернетом на сервере.  
  
 [Ведение журнала в задаче «Скрипт»](../../integration-services/extending-packages-scripting/task/logging-in-the-script-task.md)  
 Регистрирует число элементов, обработанных задачей в активных регистраторах.  
  
  

