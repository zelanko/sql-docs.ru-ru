---
title: Создание тестовых случаев (SybaseToSQL) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Tester component,Test Case Wizard
ms.assetid: b52dfd93-95af-4299-bc8f-83f2a7a6a518
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 95a6724ab836fb3dddb54fadc82821ad68f29e98
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47746362"
---
# <a name="creating-test-cases-sybasetosql"></a>Создание тестовых случаев (SybaseToSQL)
Создание теста с помощью мастера тестового случая. Этот мастер позволяет создавать тестовые случаи, выбирая и проверите объектов и путем указания параметров тестирования.  
  
## <a name="starting-the-test-case-wizard"></a>Запуск мастера тестового случая  
Для запуска мастера тестового случая выберите **новый тестовый случай...** из **тест-инженер** меню.  
  
При запуске, мастер ищет ssmatester2005db базы данных или ssmatester2008db (в зависимости от типа проекта) на исходном сервере Sybase. Это расширение схемы тест-инженер, используемой для хранения вспомогательных объектов. Если мастер тестового случая не может найти ssmatester2005db или ssmatester2008db, отображается диалоговое окно, которое предлагает для создания базы данных расширения тест-инженер. (Такая ситуация обычно возникает во время первого запуска SSMA тест-инженер.)  
  
Если появится диалоговое окно, нажмите кнопку **Да** для создания базы данных Sybase тест-инженер на исходном сервере. Затем новый диалоговое окно будет отображаться, где следует добавить одно или несколько устройств, на котором выполняется поиск новой базы данных тест-инженер. Нажмите кнопку **добавить** для добавления устройства. В **выделения пространства для базы данных тест-инженер** диалоговое окно, выберите устройство и укажите размер, используемый базой данных тест-инженер. Кроме того можно задать отдельное устройство для журналов базы данных. Обратите внимание на то, что требуются привилегии Sybase на создание баз данных.  
  
## <a name="overview-of-creating-test-cases-using-the-wizard"></a>Общие сведения о создании тестовых случаев с помощью мастера  
Процесс создания тестового случая состоит из пяти шагов:  
  
1.  [Инициализация тестовых случаев &#40;SybaseToSQL&#41;](../../ssma/sybase/initializing-test-cases-sybasetosql.md).  
  
2.  [Выбор и настройка объектов для тестирования &#40;SybaseToSQL&#41;](../../ssma/sybase/selecting-and-configuring-objects-to-test-sybasetosql.md).  
  
3.  [Выбор и настройка обрабатываемых объектов &#40;SybaseToSQL&#41;](../../ssma/sybase/selecting-and-configuring-affected-objects-sybasetosql.md).  
  
4.  [Настройка порядка вызовов &#40;SybaseToSQL&#41;](../../ssma/sybase/customizing-calls-order-sybasetosql.md).  
  
5.  [Завершение подготовки тестовых случаев &#40;SybaseToSQL&#41;](../../ssma/sybase/finishing-test-case-preparation-sybasetosql.md).  
  
## <a name="see-also"></a>См. также  
[Тестирование объектов базы данных после миграции &#40;SybaseToSQL&#41;](../../ssma/sybase/testing-migrated-database-objects-sybasetosql.md)  
  
