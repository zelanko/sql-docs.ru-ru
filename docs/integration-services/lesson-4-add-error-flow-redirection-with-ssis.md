---
title: Урок 4. Добавление перенаправления потока ошибок с помощью служб SSIS | Документация Майкрософт
ms.custom: ''
ms.date: 01/07/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: 0c8dbda2-75e3-4278-9b4e-dcd220c92522
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 43c841010b70599803c71fd6307cfb68464b7265
ms.sourcegitcommit: e2fa721b6f46c18f1825dd1b0d56c0a6da1b2be1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/11/2019
ms.locfileid: "54211005"
---
# <a name="lesson-4-add-error-flow-redirection-with-ssis"></a>Урок 4. Добавление перенаправления потока ошибок с помощью служб SSIS

Для обработки ошибок, которые могут возникать в процессе преобразования, службы [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] позволяют указать, как следует обрабатывать данные отдельных компонентов и столбцов, которые [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] не могут преобразовать. Можно проигнорировать ошибки в определенных столбцах, перенаправить всю строку с ошибкой или завершить работу компонента с ошибкой. По умолчанию для компонентов в службах [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] указано завершение работы при возникновении ошибки. Завершение работы компонента с ошибкой, в свою очередь, приводит к сбою в работе пакета и остановке обработки.  
  
Вместо прекращения выполнения пакетов при возникновении ошибок рекомендуется обрабатывать потенциальные ошибки обработки по мере их возникновения. Один из вариантов — игнорировать все сбои, чтобы пакеты всегда выполнялись успешно. Можно также перенаправить строку с ошибкой по другому пути обработки, где эти данные и ошибки можно сохранить, изучить или обработать повторно.  
  
На этом занятии предстоит создать копию пакета, разработанного в разделе [Занятие 3. Добавление журналов с помощью служб SSIS](../integration-services/lesson-3-add-logging-with-ssis.md). При работе с этим новым пакетом создается поврежденная версия одного из файлов образцов данных. Повреждение файла вызывает ошибку обработки при выполнении пакета.  
  
Чтобы обработать данные об ошибках, добавляется и настраивается назначение неструктурированного файла, записывающее все строки с ошибками в файл ошибок. 
  
Прежде чем [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] запишут данные об ошибке в файл, следует включить компонент скрипта, получающий описания ошибки. Затем следует перенастроить преобразование "Уточняющий запрос ключа валюты" таким образом, чтобы перенаправлять все данные, обработка которых невозможна, в преобразование "Скрипт".  
  
## <a name="prerequisites"></a>предварительные требования

> [!NOTE]
> Ознакомьтесь с [предварительными требованиями для занятия 1](../integration-services/lesson-1-create-a-project-and-basic-package-with-ssis.md#prerequisites), если вы еще не сделали этого.
 
## <a name="lesson-task"></a>Задача занятия
Это занятие содержит следующие задачи.  
  
-   [Шаг 1. Копирование пакета занятия 3](../integration-services/lesson-4-1-copying-the-lesson-3-package.md)  
  
-   [Шаг 2. Создание поврежденного файла](../integration-services/lesson-4-2-creating-a-corrupted-file.md)  
  
-   [Шаг 3. Добавление перенаправления потока ошибок](../integration-services/lesson-4-3-adding-error-flow-redirection.md)  
  
-   [Шаг 4. Добавление назначения "Неструктурированный файл"](../integration-services/lesson-4-4-adding-a-flat-file-destination.md)  
  
-   [Шаг 5. Тестирование учебного пакета занятия 4](../integration-services/lesson-4-5-testing-the-lesson-4-tutorial-package.md)  
  
## <a name="start-the-lesson"></a>Начало занятия  
[Шаг 1. Копирование пакета занятия 3](../integration-services/lesson-4-1-copying-the-lesson-3-package.md)  
  
  
  
