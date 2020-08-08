---
title: Тестирование перенесенных объектов базы данных (OracleToSQL) | Документация Майкрософт
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: f03ef5e1-66e6-4c84-ada2-252dd5ada82f
author: nahk-ivanov
ms.author: alexiva
manager: alexiva
ms.openlocfilehash: 9e7c63986cde88c7a1ccbf67f8dd3751bb6d41b0
ms.sourcegitcommit: e8f6c51d4702c0046aec1394109bc0503ca182f0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/07/2020
ms.locfileid: "87932835"
---
# <a name="testing-migrated-database-objects-oracletosql"></a>Тестирование объектов баз данных после миграции (OracleToSQL)
[!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Помощник по миграции для тестера Oracle (SSMA Tester) автоматически проверяет преобразование объектов базы данных и перенос данных, выполняемый SSMA. После завершения миграции SSMA Используйте тестер SSMA, чтобы убедиться, что преобразованные объекты работают одинаково и все данные были переданы должным образом.  
  
С помощью тестера SSMA можно проверить следующие типы объектов:  
  
-   Таблицы  
  
-   Хранимые процедуры, включая Упакованные процедуры.  
  
-   Определяемые пользователем функции, включая упакованные функции.  
  
-   Представления.  
  
-   Автономные инструкции.  
  
Тестер SSMA выполняет объекты, выбранные для тестирования в Oracle, и их аналоги в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . После этого он сравнивает результаты в соответствии со следующими критериями:  
  
-   Совпадают ли изменения в данных таблицы?  
  
-   Совпадают ли значения выходных параметров для процедур и функций?  
  
-   Функции Do возвращают одинаковые результаты?  
  
-   Совпадают ли результирующие наборы?  
  
> [!NOTE]  
> ВНИМАНИЕ! Никогда не используйте SSMA Tester в рабочих системах. Во время выполнения тестера изменяются исходная схема и данные. В то же время полное восстановление исходного состояния может оказаться невозможным для некоторых типов протестированного кода.  
  
## <a name="prerequisites"></a>Предварительные требования  
Если вы хотите использовать SSMA Tester, установите пакет расширения SSMA Oracle с включенным параметром **Install Tester Database** .  
  
Чтобы включить Сравнение результирующих данных таблицы, задайте для параметра **создать столбец ROWID** значение **Да** перед началом преобразования схемы. SSMA добавит столбец ROWID во все таблицы во время выполнения команды **Convert Schema** .  
  
Кроме того, проверьте следующее:  
  
-   Клиентские средства Oracle устанавливаются на компьютере, на котором [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполняется.  
  
-   Интеграция со средой CLR включена на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ядро СУБД.  
  
Обратите внимание, что текущая версия тестера SSMA не поддерживает параллельное выполнение разными пользователями на одном исходном или целевом сервере.  
  
## <a name="getting-started"></a>Начало работы  
[Создание тестовых случаев &#40;OracleToSQL&#41;](../../ssma/oracle/creating-test-cases-oracletosql.md)  
  
## <a name="see-also"></a>См. также:  
[Установка компонентов SSMA на SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/installing-ssma-components-on-sql-server-oracletosql.md)  
[Параметры проекта &#40;преобразование&#41; &#40;OracleToSQL&#41;](../../ssma/oracle/project-settings-conversion-oracletosql.md)  
  
