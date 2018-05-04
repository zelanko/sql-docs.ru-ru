---
title: Создание тестовых случаев (OracleToSQL) | Документы Microsoft
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-oracle
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Test Case Wizard
ms.assetid: 22f38901-ec35-4707-a911-784e6ad8dafb
caps.latest.revision: 7
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: 92d5b358d8e401e5963470151e48d72c930c7030
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="creating-test-cases-oracletosql"></a>Создание тестовых случаев (OracleToSQL)
Мастер тестового случая для создания теста. Этот мастер позволяет создавать тестовые случаи, при выборе тестирования и проверки объектов, с помощью параметров тестирования.  
  
## <a name="starting-the-test-case-wizard"></a>Запуск мастера тестового случая  
Для запуска мастера тестового случая выберите **новый тестовый случай...** из **тест-инженер** меню.  
  
При запуске мастер выполняет поиск схемы SSMATESTER_ORACLE на исходном сервере Oracle. Это расширение схемы тест-инженер, используемой для хранения вспомогательных объектов. Если мастер тестового случая не удается найти SSMATESTER_ORACLE, он отображает диалоговое окно, которое предлагает для создания схемы. (Такой ситуации обычно происходит во время первого выполнения тест-инженер SSMA).  
  
Если появляется диалоговое окно, нажмите кнопку **Да** для создания схемы SSMATESTER_ORACLE на исходном сервере. Обратите внимание, что необходимо иметь права Oracle для создания нового пользователя и создания объектов в схеме этого пользователя.  
  
## <a name="overview-of-creating-test-cases-using-the-wizard"></a>Общие сведения о создании тестовых случаев с помощью мастера  
Процесс создания тестового случая состоит из пяти шагов:  
  
1.  [Инициализация тестовых случаев &#40;OracleToSQL&#41;](../../ssma/oracle/initializing-test-cases-oracletosql.md)  
  
2.  [Выбор и настройка объектов для тестирования &#40;OracleToSQL&#41;](../../ssma/oracle/selecting-and-configuring-objects-to-test-oracletosql.md)  
  
3.  [Выбор и настройка затронутые объекты &#40;OracleToSQL&#41;](../../ssma/oracle/selecting-and-configuring-affected-objects-oracletosql.md)  
  
4.  [Настройка порядка вызовов &#40;OracleToSQL&#41;](../../ssma/oracle/customizing-calls-order-oracletosql.md)  
  
5.  [Завершение подготовки тестовый случай &#40;OracleToSQL&#41;](../../ssma/oracle/finishing-test-case-preparation-oracletosql.md)  
  
## <a name="see-also"></a>См. также  
[Тестирование перенесенные объекты базы данных &#40;OracleToSQL&#41;](../../ssma/oracle/testing-migrated-database-objects-oracletosql.md)  
  
