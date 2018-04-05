---
title: Выполнение тестовых случаев (SybaseToSQL) | Документы Microsoft
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
- Tester Component,Execution Steps
ms.assetid: 195ffdef-cfde-4bf4-a3ae-e7402bb07972
caps.latest.revision: 6
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0b78d26a492a73964c39b15c678103537cd9abe1
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="running-test-cases-sybasetosql"></a>Выполнение тестовых случаев (SybaseToSQL)
Когда SSMA тест-инженер запускает тест, он выполняет объекты, выбранные для тестирования и создает отчет о результатах проверки. Если результаты совпадают на обеих платформах, проверка выполнена успешно. Соответствие объектов между Sybase и [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] определяется в соответствии с параметрами соответствие схемы для текущего проекта SSMA.  
  
Необходимые требования для успешного завершения проверки — преобразуются и загружаются в целевой базе данных все объекты Sybase. Кроме того данные таблицы следует перенести, чтобы синхронизировать содержимое таблиц на обеих платформах.  
  
## <a name="run-test-case"></a>Выполнение тестового случая  
Чтобы запустить подготовленный тестового случая:  
  
1.  Нажмите кнопку **запуска** кнопки.  
  
2.  В **соединиться Sybase** диалоговое окно, введите сведения о соединении и нажмите кнопку **Connect**.  
  
После завершения теста создается отчет тестовых случаев. Нажмите кнопку **отчетов** кнопку, чтобы просмотреть [просмотра отчетов тестовый случай &#40; SybaseToSQL &#41; ](../../ssma/sybase/viewing-test-case-reports-sybasetosql.md). Результат теста (тестовый случай отчет), автоматически сохраняются в [репозиториев тестирования с помощью &#40; SybaseToSQL &#41; ](../../ssma/sybase/using-test-repositories-sybasetosql.md) для последующего использования.  
  
## <a name="test-case-execution-steps"></a>Шаги выполнения тестового случая  
  
### <a name="prerequisites"></a>предварительные требования  
SSMA тест-инженер проверяет, если выполнены все предварительные требования для выполнения тестов перед запуском теста. Если некоторые условия не соблюдены, появится сообщение об ошибке.  
  
### <a name="initialization"></a>Инициализация  
На этом этапе SSMA инженер-испытатель создает вспомогательные объекты (таблицы, триггеры и представления) обоих Sybase и [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Они позволяют трассировки изменений, внесенных в измененных таблиц, выбранные для проверки, если используется режим сравнения таблицы **изменяет только**.  
  
Предположим, что проверенных таблица называется USER_TABLE. Для такой таблицы следующие вспомогательные объекты создаются в Sybase.  
  
Следующие объекты создаются в Sybase в базу данных SSMATESTER2005db или SSMATESTER2008db и [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] ssmatesterdb_syb базы данных.  
  
|Имя|Тип|Description|  
|--------|--------|---------------|  
|USER_TABLE$ Trg|Триггер|Аудит изменений в таблице проверенных триггер.|  
|USER_TABLE$ Aud|Table|Таблица сохранения строки удаляются и перезаписаны.|  
|USER_TABLE$ AudID|Table|Таблица сохранения новых и измененных строк.|  
|USER_TABLE|Просмотр|Упрощенное представление изменения таблиц.|  
|$ USER_TABLE новые|Просмотр|Упрощенное представление вставленные и перезаписать строки.|  
|USER_TABLE$ new_id|Просмотр|Идентификация вставленные и измененные строки.|  
|$ USER_TABLE старые|Просмотр|Упрощенное представление строки удаляются и перезаписаны.|  
  
Следующий объект создается в базе данных таблицы, проверенных на Sybase и [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
|Имя|Тип|Description|  
|--------|--------|---------------|  
|USER_TABLE$ Trg|Триггер|Аудит изменений в таблице проверенных триггер.|  
  
### <a name="test-object-calls"></a>Тест вызывает объект  
На этом этапе тест-инженер SSMA вызывает каждому объекту, выбранному для тестирования, сравниваются результаты и показывает отчет.  
  
### <a name="finalization"></a>Завершение  
Во время завершения инженер-испытатель SSMA очищает вспомогательные объекты, созданные в **инициализации** шаг.  
  
## <a name="next-step"></a>Следующий шаг  
[Просмотр отчетов тестовый случай &#40; SybaseToSQL &#41;](../../ssma/sybase/viewing-test-case-reports-sybasetosql.md)  
  
## <a name="see-also"></a>См. также:  
[Выбор и настройка объектов для тестирования &#40; SybaseToSQL &#41;](../../ssma/sybase/selecting-and-configuring-objects-to-test-sybasetosql.md)  
[Выбор и настройка затронутые объекты &#40; SybaseToSQL &#41;](../../ssma/sybase/selecting-and-configuring-affected-objects-sybasetosql.md)  
[Тестирование миграции объектов базы данных &#40; SybaseToSQL &#41;](../../ssma/sybase/testing-migrated-database-objects-sybasetosql.md)  
  
