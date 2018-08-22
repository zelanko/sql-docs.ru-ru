---
title: Тестирование миграции объектов базы данных (SybaseToSQL) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 4937f6b4-86bd-4070-88df-3d216306c33a
caps.latest.revision: 7
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: ac7654f43f2d453ad0e55a0a7ebcfee79ac2c91c
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/14/2018
ms.locfileid: "40395330"
---
# <a name="testing-migrated-database-objects-sybasetosql"></a>Тестирование объектов базы данных после миграции (SybaseToSQL)
Microsoft SQL Server Migration Assistant для Sybase Tester (тестер SSMA) автоматически проверяет преобразования объекта базы данных и переноса данных, произведенные SSMA. После завершения всех шагов миграции SSMA позволяет убедиться, что преобразованные объекты работают так же, как и все данные было передано надлежащим образом тест-инженер SSMA.  
  
> [!NOTE]  
> Тест-инженер компонент отключен в случае подключения к Azure.  
  
Следующие типы объектов можно проверить с помощью SSMA тестера:  
  
-   Таблицы  
  
-   Хранимые процедуры  
  
-   Представления.  
  
-   Автономный инструкции.  
  
Тест-инженер SSMA выполняет объектов, выбранных для тестирования на Sybase и их аналогов в SQL Server. После этого он сравнивает результаты в соответствии со следующим критериям:  
  
-   Табличные данные идентичны изменения?  
  
-   Значения выходных параметров для процедур и функций идентичны?  
  
-   У функции возвращают одинаковые результаты?  
  
-   Соответствуют ли результат наборы идентичны?  
  
> [!NOTE]  
> Внимание! Никогда не используйте SSMA тест-инженер в рабочих системах. Во время выполнения тест-инженер изменяются исходной схемы и данных. В то же время полного восстановления исходного состояния может оказаться невозможным для некоторых типов тестируемого кода.  
  
## <a name="prerequisites"></a>предварительные требования  
Если вы хотите использовать тест-инженер SSMA, установить пакет расширения SSMA Sybase с **установить базы данных тест-инженер** включенным параметром.  
  
Кроме того проверьте следующее.  
  
-   Поставщик OLE DB для Sybase устанавливается на компьютере, где [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполняется.  
  
-   Интеграция Common Language Runtime (CLR) включена [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] компонент Database Engine.  
  
Обратите внимание на то, что текущая версия SSMA Tester не поддерживает параллельное выполнение разными пользователями на одном исходном или целевом сервере.  
  
## <a name="getting-started"></a>Приступая к работе  
[Создание тестовых случаев &#40;SybaseToSQL&#41;](../../ssma/sybase/creating-test-cases-sybasetosql.md)  
  
## <a name="see-also"></a>См. также  
[Установка компонентов SSMA в SQL Server &#40;SybaseToSQL&#41;](../../ssma/sybase/installing-ssma-components-on-sql-server-sybasetosql.md)  
[Параметры проекта &#40;преобразования&#41; &#40;SybaseToSQL&#41;](../../ssma/sybase/project-settings-conversion-sybasetosql.md)  
  
