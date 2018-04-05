---
title: Создание тестовых случаев (SybaseToSQL) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-sybase
ms.reviewer: ''
ms.suite: sql
ms.technology:
- sql-ssma
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Tester component,Test Case Wizard
ms.assetid: b52dfd93-95af-4299-bc8f-83f2a7a6a518
caps.latest.revision: 5
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8028f170d5f3154b9874cda16cc18bd7b36a84b8
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="creating-test-cases-sybasetosql"></a>Создание тестовых случаев (SybaseToSQL)
Мастер тестового случая для создания теста. Этот мастер позволяет создавать тестовые случаи, при выборе тестирования и проверки объектов, с помощью параметров тестирования.  
  
## <a name="starting-the-test-case-wizard"></a>Запуск мастера тестового случая  
Для запуска мастера тестового случая выберите **новый тестовый случай...** из **тест-инженер** меню.  
  
При запуске мастер анализирует базы данных ssmatester2005db или ssmatester2008db (в зависимости от типа проекта) на исходном сервере Sybase. Это расширение схемы тест-инженер, используемой для хранения вспомогательных объектов. Если мастер тестового случая не удается найти ssmatester2005db или ssmatester2008db, он отображает диалоговое окно, которое предлагает для создания базы данных расширения тест-инженер. (Такой ситуации обычно происходит во время первого выполнения тест-инженер SSMA).  
  
Если появляется диалоговое окно, нажмите кнопку **Да** для создания базы данных Sybase инженер-испытатель на исходном сервере. Новое диалоговое окно появляется здесь необходимо добавить одно или несколько устройств, на котором выполняется поиск новых тест-инженер базы данных. Нажмите кнопку **добавить** для добавления устройства. В **выделения места для базы данных тест-инженер** диалогового окна выберите устройства и укажите размер, тест-инженер для базы данных. Кроме того можно задать отдельное устройство для журналов базы данных. Обратите внимание, что необходимо иметь Sybase права на создание баз данных.  
  
## <a name="overview-of-creating-test-cases-using-the-wizard"></a>Общие сведения о создании тестовых случаев с помощью мастера  
Процесс создания тестового случая состоит из пяти шагов:  
  
1.  [Инициализация тестовых случаев &#40; SybaseToSQL &#41; ](../../ssma/sybase/initializing-test-cases-sybasetosql.md).  
  
2.  [Выбор и настройка объектов для тестирования &#40; SybaseToSQL &#41; ](../../ssma/sybase/selecting-and-configuring-objects-to-test-sybasetosql.md).  
  
3.  [Выбор и настройка затронутые объекты &#40; SybaseToSQL &#41; ](../../ssma/sybase/selecting-and-configuring-affected-objects-sybasetosql.md).  
  
4.  [Настройка порядка вызовов &#40; SybaseToSQL &#41; ](../../ssma/sybase/customizing-calls-order-sybasetosql.md).  
  
5.  [Завершение подготовки тестового случая &#40; SybaseToSQL &#41; ](../../ssma/sybase/finishing-test-case-preparation-sybasetosql.md).  
  
## <a name="see-also"></a>См. также:  
[Тестирование миграции объектов базы данных &#40; SybaseToSQL &#41;](../../ssma/sybase/testing-migrated-database-objects-sybasetosql.md)  
  
