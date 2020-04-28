---
title: Тестирование перенесенных объектов базы данных (SybaseToSQL) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 4937f6b4-86bd-4070-88df-3d216306c33a
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 6fb469dfcaaec33a03681bfb64f411851df0400e
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68020912"
---
# <a name="testing-migrated-database-objects-sybasetosql"></a>Тестирование объектов базы данных после миграции (SybaseToSQL)
Помощник по миграции Microsoft SQL Server для тестера Sybase (SSMA Tester) автоматически проверяет преобразование объектов базы данных и перенос данных, выполняемый SSMA. После завершения миграции SSMA Используйте тестер SSMA, чтобы убедиться, что преобразованные объекты работают одинаково и все данные были переданы должным образом.  
  
> [!NOTE]  
> Компонент "тест-инженер" отключен в случае подключения к Azure.  
  
С помощью тестера SSMA можно проверить следующие типы объектов:  
  
-   Таблицы  
  
-   Хранимые процедуры  
  
-   Представления.  
  
-   Автономные инструкции.  
  
Тестер SSMA выполняет объекты, выбранные для тестирования в Sybase, и их аналоги в SQL Server. После этого он сравнивает результаты в соответствии со следующими критериями:  
  
-   Совпадают ли изменения в данных таблицы?  
  
-   Совпадают ли значения выходных параметров для процедур и функций?  
  
-   Функции Do возвращают одинаковые результаты?  
  
-   Совпадают ли результирующие наборы?  
  
> [!NOTE]  
> Обратит! Никогда не используйте SSMA Tester в рабочих системах. Во время выполнения тестера изменяются исходная схема и данные. В то же время полное восстановление исходного состояния может оказаться невозможным для некоторых типов протестированного кода.  
  
## <a name="prerequisites"></a>Предварительные требования  
Если вы хотите использовать SSMA Tester, установите пакет расширений SSMA Sybase с включенным параметром **Install Tester Database** .  
  
Кроме того, проверьте следующее:  
  
-   На компьютере, на котором [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполняется, установлен поставщик OLE DB Sybase.  
  
-   Интеграция со средой CLR включена на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ядро СУБД.  
  
Обратите внимание, что текущая версия тестера SSMA не поддерживает параллельное выполнение разными пользователями на одном исходном или целевом сервере.  
  
## <a name="getting-started"></a>Приступая к работе  
[Создание тестовых случаев &#40;SybaseToSQL&#41;](../../ssma/sybase/creating-test-cases-sybasetosql.md)  
  
## <a name="see-also"></a>См. также:  
[Установка компонентов SSMA на SQL Server &#40;SybaseToSQL&#41;](../../ssma/sybase/installing-ssma-components-on-sql-server-sybasetosql.md)  
[Параметры проекта &#40;преобразование&#41; &#40;SybaseToSQL&#41;](../../ssma/sybase/project-settings-conversion-sybasetosql.md)  
  
