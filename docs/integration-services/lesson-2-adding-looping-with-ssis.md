---
title: "Занятие 2: Добавление циклов со службами SSIS | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: integration-services
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: 01f2ed61-1e5a-4ec6-b6a6-2bd070c64077
caps.latest.revision: 32
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 8559dc3afb5f347555b9b21b61abc50765fd92c4
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="lesson-2-adding-looping-with-ssis"></a>Занятие 2. Добавление циклов с помощью служб SSIS
При работе над разделом [Занятие 1. Создание проекта и основного пакета с помощью служб SSIS](../integration-services/lesson-1-create-a-project-and-basic-package-with-ssis.md)был создан пакет, в котором данные извлекались из отдельного источника неструктурированного файла, преобразовывались с помощью преобразований "Уточняющий запрос" и затем загружались в таблицу фактов **FactCurrency** образца базы данных **AdventureWorksDW2012** .  
  
Однако в процессе извлечения, преобразования и загрузки (ETL) редко используется отдельный неструктурированный файл. Как правило, в процессе ETL данные извлекаются из нескольких источников неструктурированного файла. Извлечение данных из нескольких источников требует итеративного потока управления. Одной из самых ожидаемых возможностей служб [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] является способность легко добавлять повторения или циклы в пакеты.  
  
[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] предоставляют два типа контейнеров для циклов по пакетам: контейнер «цикл по каждому элементу» и контейнер «цикл по элементам». В контейнере «цикл по каждому элементу» для выполнения циклической обработки используется перечислитель, а в контейнере «цикл по элементам» чаще используется переменное выражение. На этом занятии рассматривается контейнер «цикл по каждому элементу».  
  
При помощи этого контейнера поток управления в пакете может повторяться для каждого элемента указанного перечислителя. Используя контейнер «цикл по каждому элементу», можно перечислять:  
  
-   Строки наборов записей ADO  
  
-   Данные схемы ADO.NET:  
  
-   структуры файлов и каталогов;  
  
-   системные, пакетные и пользовательские переменные;  
  
-   перечисляемые объекты, содержащиеся в переменной;  
  
-   элементы коллекции;  
  
-   узлы в выражении языка пути XML (XPath);  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Управляющие объекты (SMO)  
  
На этом занятии предстоит изменить простой пакет ETL, созданный на занятии 1, с целью использования возможностей контейнера «цикл по каждому элементу». Кроме того, предстоит задать пользовательские пакетные переменные, чтобы в пакете учебника могли последовательно обрабатываться все неструктурированные файлы в папке. Если предыдущее занятие не выполнялось, можно скопировать завершенный пакет занятия 1, который включен в учебник.  
  
На этом занятии будет изменяться только поток управления, поток данных не рассматривается.  
  
> [!IMPORTANT]  
> Для выполнения упражнений этого учебника потребуется образец базы данных **AdventureWorksDW2012** . Дополнительные сведения об установке и развертывании **AdventureWorksDW2012**см. в разделе [Проект образцов продуктов службы Reporting Services на сайте CodePlex](http://go.microsoft.com/fwlink/p/?LinkID=526910).  
  
## <a name="lesson-tasks"></a>Задачи занятия  
Это занятие содержит следующие задачи.  
  
-   [Шаг 1. Копирование пакета занятия 1](../integration-services/lesson-2-1-copying-the-lesson-1-package.md)  
  
-   [Шаг 2. Добавление и настройка контейнера "цикл по каждому элементу"](../integration-services/lesson-2-2-adding-and-configuring-the-foreach-loop-container.md)  
  
-   [Шаг 3. Изменение диспетчера соединений с неструктурированными файлами](../integration-services/lesson-2-3-modifying-the-flat-file-connection-manager.md)  
  
-   [Шаг 4. Проверка учебного пакета, созданного на занятии 2](../integration-services/lesson-2-4-testing-the-lesson-2-tutorial-package.md)  
  
## <a name="start-the-lesson"></a>Начало занятия  
[Шаг 1. Копирование пакета занятия 1](../integration-services/lesson-2-1-copying-the-lesson-1-package.md)  
  
## <a name="see-also"></a>См. также:  
[Контейнер «цикл по элементам»](../integration-services/control-flow/for-loop-container.md)  
  
  
  

