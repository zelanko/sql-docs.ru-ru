---
title: Урок 2. Добавление циклов с помощью служб SSIS | Документация Майкрософт
ms.custom: ''
ms.date: 01/03/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: 01f2ed61-1e5a-4ec6-b6a6-2bd070c64077
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ccd3be3203aae382cda239ed6d7bdc2fa224923b
ms.sourcegitcommit: e8af8cfc0bb51f62a4f0fa794c784f1aed006c71
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/26/2019
ms.locfileid: "71296055"
---
# <a name="lesson-2-add-looping-with-ssis"></a>Урок 2. Добавление циклов с помощью служб SSIS

[!INCLUDE[ssis-appliesto](../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]



В разделе [Занятие 1. Создание проекта и простого пакета с помощью служб SSIS](../integration-services/lesson-1-create-a-project-and-basic-package-with-ssis.md) вы создали пакет, извлекающий данные из отдельного источника неструктурированных файлов. Затем эти данные преобразовывались с помощью преобразований "Уточняющий запрос". Наконец, пакет загружал данные в копию таблицы фактов **FactCurrencyRate** в образце базы данных **AdventureWorksDW2012**.  
  
В процессе извлечения, преобразования и загрузки данные извлекаются из нескольких источников неструктурированных файлов. Извлечение данных из нескольких источников требует итеративного потока управления. [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] может легко добавить итерацию или циклы в пакеты.  
  
[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] предоставляют два типа контейнеров для циклов по пакетам: контейнер «цикл по каждому элементу» и контейнер «цикл по элементам». В контейнере "Цикл по каждому элементу" для выполнения циклической обработки используется перечислитель, а в контейнере "Цикл по элементам" чаще используется переменное выражение. На этом занятии рассматривается контейнер «цикл по каждому элементу».  
  
При помощи этого контейнера поток управления в пакете может повторяться для каждого элемента указанного перечислителя. Используя контейнер «цикл по каждому элементу», можно перечислять:  
  
-   Строки наборов записей ADO  
  
-   Данные схемы ADO.NET:  
  
-   структуры файлов и каталогов;  
  
-   системные, пакетные и пользовательские переменные;  
  
-   перечисляемые объекты в переменной;  
  
-   элементы коллекции;  
  
-   узлы в выражении языка пути XML (XPath);  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Управляющие объекты (SMO)  
  
На этом занятии вы измените пакет извлечения, преобразования и загрузки из занятия 1, чтобы использовать контейнер "Цикл по каждому элементу" и определенную пользователем переменную для пакета. Эта переменная затем используется для итерации по соответствующим файлам в папке примера.   
  
На этом занятии будет изменяться только поток управления, поток данных не рассматривается.  
  
> [!NOTE]  
> Ознакомьтесь с [предварительными требованиями для занятия 1](../integration-services/lesson-1-create-a-project-and-basic-package-with-ssis.md#prerequisites), если вы еще не сделали этого.

## <a name="lesson-tasks"></a>Задачи занятия  
Это занятие содержит следующие задачи.  
  
-   [Шаг 1. Копирование пакета занятия 1](../integration-services/lesson-2-1-copying-the-lesson-1-package.md)  
  
-   [Шаг 2. Добавление и настройка контейнера "Цикл по каждому элементу"](../integration-services/lesson-2-2-adding-and-configuring-the-foreach-loop-container.md)  
  
-   [Шаг 3. Изменение диспетчера подключений с неструктурированными файлами](../integration-services/lesson-2-3-modifying-the-flat-file-connection-manager.md)  
  
-   [Шаг 4. Тестирование учебного пакета занятия 2](../integration-services/lesson-2-4-testing-the-lesson-2-tutorial-package.md)  
  
## <a name="start-the-lesson"></a>Начало занятия  
[Шаг 1. Копирование пакета занятия 1](../integration-services/lesson-2-1-copying-the-lesson-1-package.md)  
  
## <a name="see-also"></a>См. также раздел  
[Контейнер "Цикл по элементам"](../integration-services/control-flow/for-loop-container.md)  
  
  
  
