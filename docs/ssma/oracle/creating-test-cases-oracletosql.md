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
manager: shamikg
ms.openlocfilehash: 697f7049a60aa7ae2b8c89d1fb6c5ce8e3d29312
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68266127"
---
# <a name="creating-test-cases-oracletosql"></a>Создание тестовых случаев (OracleToSQL)
Используйте мастер тестовых случаев для создания теста. Этот мастер позволяет создавать тестовые случаи, выбрав проверенные и проверенные объекты и указав параметры тестирования.  
  
## <a name="starting-the-test-case-wizard"></a>Запуск мастера тестовых случаев  
Чтобы запустить мастер тестовых случаев, щелкните **создать тестовый случай...** в меню **Тестер** .  
  
При запуске мастер выполняет поиск SSMATESTER_ORACLE схемы на исходном сервере Oracle. Это схема расширения тестеров, используемая для хранения вспомогательных объектов. Если мастер тестовых случаев не может найти SSMATESTER_ORACLE, откроется диалоговое окно, в котором предлагается создать схему. (Эта ситуация обычно возникает во время первого запуска тест-инженера SSMA.)  
  
Если появится диалоговое окно, нажмите кнопку **Да** , чтобы создать схему SSMATESTER_ORACLE на исходном сервере. Обратите внимание, что у вас должны быть права Oracle для создания нового пользователя и создания объектов в схеме этого пользователя.  
  
## <a name="overview-of-creating-test-cases-using-the-wizard"></a>Общие сведения о создании тестовых случаев с помощью мастера  
Процесс создания тестового случая состоит из пяти шагов.  
  
1.  [Инициализация тестовых случаев &#40;OracleToSQL&#41;](../../ssma/oracle/initializing-test-cases-oracletosql.md)  
  
2.  [Выбор и настройка объектов для тестирования &#40;OracleToSQL&#41;](../../ssma/oracle/selecting-and-configuring-objects-to-test-oracletosql.md)  
  
3.  [Выбор и настройка затронутых объектов &#40;OracleToSQL&#41;](../../ssma/oracle/selecting-and-configuring-affected-objects-oracletosql.md)  
  
4.  [Настройка порядка вызовов &#40;OracleToSQL&#41;](../../ssma/oracle/customizing-calls-order-oracletosql.md)  
  
5.  [Завершение подготовки тестового случая &#40;OracleToSQL&#41;](../../ssma/oracle/finishing-test-case-preparation-oracletosql.md)  
  
## <a name="see-also"></a>См. также:  
[Тестирование перенесенных объектов базы данных &#40;OracleToSQL&#41;](../../ssma/oracle/testing-migrated-database-objects-oracletosql.md)  
  
