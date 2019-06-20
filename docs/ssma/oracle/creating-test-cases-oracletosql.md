---
title: Создание тестовых случаев (OracleToSQL) | Документация Майкрософт
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Test Case Wizard
ms.assetid: 22f38901-ec35-4707-a911-784e6ad8dafb
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: a2c1bd3fea167a784d86f7e323566f73c3a01f86
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63287705"
---
# <a name="creating-test-cases-oracletosql"></a>Создание тестовых случаев (OracleToSQL)
Создание теста с помощью мастера тестового случая. Этот мастер позволяет создавать тестовые случаи, выбирая и проверите объектов и путем указания параметров тестирования.  
  
## <a name="starting-the-test-case-wizard"></a>Запуск мастера тестового случая  
Для запуска мастера тестового случая выберите **новый тестовый случай...**  из **тест-инженер** меню.  
  
При запуске, мастер ищет схемы SSMATESTER_ORACLE на исходном сервере Oracle. Это расширение схемы тест-инженер, используемой для хранения вспомогательных объектов. Если мастер тестового случая не может найти SSMATESTER_ORACLE, отображается диалоговое окно, которое предлагает для создания схемы. (Такая ситуация обычно возникает во время первого запуска SSMA тест-инженер.)  
  
Если появится диалоговое окно, нажмите кнопку **Да** для создания схемы SSMATESTER_ORACLE на исходном сервере. Обратите внимание на то, что требуются привилегии Oracle для создания нового пользователя и создания объектов в схеме этого пользователя.  
  
## <a name="overview-of-creating-test-cases-using-the-wizard"></a>Общие сведения о создании тестовых случаев с помощью мастера  
Процесс создания тестового случая состоит из пяти шагов:  
  
1.  [Инициализация тестовых случаев &#40;OracleToSQL&#41;](../../ssma/oracle/initializing-test-cases-oracletosql.md)  
  
2.  [Выбор и настройка объектов для тестирования &#40;OracleToSQL&#41;](../../ssma/oracle/selecting-and-configuring-objects-to-test-oracletosql.md)  
  
3.  [Выбор и настройка обрабатываемых объектов &#40;OracleToSQL&#41;](../../ssma/oracle/selecting-and-configuring-affected-objects-oracletosql.md)  
  
4.  [Настройка порядка вызовов &#40;OracleToSQL&#41;](../../ssma/oracle/customizing-calls-order-oracletosql.md)  
  
5.  [Завершение подготовки тестовых случаев &#40;OracleToSQL&#41;](../../ssma/oracle/finishing-test-case-preparation-oracletosql.md)  
  
## <a name="see-also"></a>См. также  
[Тестирование объектов базы данных после миграции &#40;OracleToSQL&#41;](../../ssma/oracle/testing-migrated-database-objects-oracletosql.md)  
  
