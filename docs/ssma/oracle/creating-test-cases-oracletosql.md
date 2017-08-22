---
title: "Создание тестовых случаев (OracleToSQL) | Документы Microsoft"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Test Case Wizard
ms.assetid: 22f38901-ec35-4707-a911-784e6ad8dafb
caps.latest.revision: 7
author: sabotta
ms.author: carlasab
manager: v-thobro
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: c40ee9da718fec017381740d69b6fa71045572bd
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="creating-test-cases-oracletosql"></a>Создание тестовых случаев (OracleToSQL)
Мастер тестового случая для создания теста. Этот мастер позволяет создавать тестовые случаи, при выборе тестирования и проверки объектов, с помощью параметров тестирования.  
  
## <a name="starting-the-test-case-wizard"></a>Запуск мастера тестового случая  
Для запуска мастера тестового случая выберите **новый тестовый случай...** из **тест-инженер** меню.  
  
При запуске мастер выполняет поиск схемы SSMATESTER_ORACLE на исходном сервере Oracle. Это расширение схемы тест-инженер, используемой для хранения вспомогательных объектов. Если мастер тестового случая не удается найти SSMATESTER_ORACLE, он отображает диалоговое окно, которое предлагает для создания схемы. (Такой ситуации обычно происходит во время первого выполнения тест-инженер SSMA).  
  
Если появляется диалоговое окно, нажмите кнопку **Да** для создания схемы SSMATESTER_ORACLE на исходном сервере. Обратите внимание, что необходимо иметь права Oracle для создания нового пользователя и создания объектов в схеме этого пользователя.  
  
## <a name="overview-of-creating-test-cases-using-the-wizard"></a>Общие сведения о создании тестовых случаев с помощью мастера  
Процесс создания тестового случая состоит из пяти шагов:  
  
1.  [Инициализация тестовых случаев &#40; OracleToSQL &#41;](../../ssma/oracle/initializing-test-cases-oracletosql.md)  
  
2.  [Выбор и настройка объектов для тестирования &#40; OracleToSQL &#41;](../../ssma/oracle/selecting-and-configuring-objects-to-test-oracletosql.md)  
  
3.  [Выбор и настройка затронутые объекты &#40; OracleToSQL &#41;](../../ssma/oracle/selecting-and-configuring-affected-objects-oracletosql.md)  
  
4.  [Настройка порядка вызовов &#40; OracleToSQL &#41;](../../ssma/oracle/customizing-calls-order-oracletosql.md)  
  
5.  [Завершение подготовки тестового случая &#40; OracleToSQL &#41;](../../ssma/oracle/finishing-test-case-preparation-oracletosql.md)  
  
## <a name="see-also"></a>См. также:  
[Тестирование миграции объектов базы данных &#40; OracleToSQL &#41;](../../ssma/oracle/testing-migrated-database-objects-oracletosql.md)  
  

