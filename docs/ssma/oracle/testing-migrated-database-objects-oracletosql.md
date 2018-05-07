---
title: Тестирование перенесенные объекты базы данных (OracleToSQL) | Документы Microsoft
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssma-oracle
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: f03ef5e1-66e6-4c84-ada2-252dd5ada82f
caps.latest.revision: 7
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: da2327f94062d81a9b80e1884deb5150be494faa
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="testing-migrated-database-objects-oracletosql"></a>Тестирование перенесенные объекты базы данных (OracleToSQL)
[!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Помощник по миграции для тест-инженера Oracle (SSMA тестировщик) автоматически проверяет преобразования объекта базы данных и переноса данных, внесенных SSMA. После завершения всех шагов миграции SSMA используйте тест-инженер SSMA для проверки, преобразованные объекты работать так же, как и все данные были перемещены должным образом.  
  
Следующие типы объектов можно проверить с помощью тестера SSMA:  
  
-   Таблицы  
  
-   Хранимые процедуры, в том числе упакованных процедур.  
  
-   Определяемые пользователем функции, включая упакованные функции.  
  
-   Представления.  
  
-   Инструкции автономный.  
  
Инженер-испытатель SSMA выполняет объектов, выбранных для тестирования на Oracle и их аналогами в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. После этого сравниваются результаты в соответствии со следующим критериям:  
  
-   Табличные данные идентичны изменения?  
  
-   Значения выходных параметров для процедуры и функции идентичны?  
  
-   Функции возвращают одинаковые результаты?  
  
-   Результирующие наборы идентичные такое  
  
> [!NOTE]  
> Внимание! Никогда не используйте тест-инженер SSMA в рабочих системах. Во время выполнения тест-инженер изменяются исходной схемы и данных. В то же время завершения восстановления исходного состояния может быть невозможно для некоторых типов протестированного кода.  
  
## <a name="prerequisites"></a>предварительные требования  
Если вы хотите использовать SSMA тестировщик, установите пакет расширения SSMA Oracle с **установки базы данных тест-инженер** включения параметра.  
  
Чтобы включить сравнение результирующих данных таблицы, задать **ROWID сформировать столбец** для параметра **Да** перед началом преобразования схемы. SSMA будет добавлен столбец ROWID ко всем таблицам во время выполнения **преобразование схемы** команды.  
  
Кроме того проверьте следующее.  
  
-   Клиентские средства Oracle, установленных на компьютере, где [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] запускает.  
  
-   Общие интеграция Language Runtime (CLR) включена на [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] компонент Database Engine.  
  
Обратите внимание, что текущая версия SSMA тест-инженер не поддерживает параллельное выполнение разными пользователями на том же исходном или целевом сервере.  
  
## <a name="getting-started"></a>Приступая к работе  
[Создание тестовых случаев &#40;OracleToSQL&#41;](../../ssma/oracle/creating-test-cases-oracletosql.md)  
  
## <a name="see-also"></a>См. также  
[Установка компонентов SSMA на SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/installing-ssma-components-on-sql-server-oracletosql.md)  
[Параметры проекта &#40;преобразования&#41; &#40;OracleToSQL&#41;](../../ssma/oracle/project-settings-conversion-oracletosql.md)  
  
