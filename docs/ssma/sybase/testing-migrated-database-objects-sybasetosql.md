---
title: Тестирование перенесенные объекты базы данных (SybaseToSQL) | Документы Microsoft
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
ms.openlocfilehash: 6f95ab1a14679d919a11fcc5a0c26554ac6120f2
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2018
ms.locfileid: "34779410"
---
# <a name="testing-migrated-database-objects-sybasetosql"></a>Тестирование перенесенные объекты базы данных (SybaseToSQL)
Microsoft SQL Server Migration Assistant для Sybase тест-инженера (SSMA тестировщик) автоматически выполняют проверку преобразования объекта базы данных и переноса данных, внесенных SSMA. После завершения всех шагов миграции SSMA используйте тест-инженер SSMA для проверки, преобразованные объекты работать так же, как и все данные были перемещены должным образом.  
  
> [!NOTE]  
> Инженер-испытатель компонент отключен в случае подключения к Azure.  
  
Следующие типы объектов можно проверить с помощью тестера SSMA:  
  
-   Таблицы  
  
-   Хранимые процедуры  
  
-   Представления.  
  
-   Инструкции автономный.  
  
Инженер-испытатель SSMA выполняет объектов, выбранных для тестирования на Sybase и их аналогами в SQL Server. После этого сравниваются результаты в соответствии со следующим критериям:  
  
-   Табличные данные идентичны изменения?  
  
-   Значения выходных параметров для процедуры и функции идентичны?  
  
-   Функции возвращают одинаковые результаты?  
  
-   Результирующие наборы идентичные такое  
  
> [!NOTE]  
> Внимание! Никогда не используйте тест-инженер SSMA в рабочих системах. Во время выполнения тест-инженер изменяются исходной схемы и данных. В то же время завершения восстановления исходного состояния может быть невозможно для некоторых типов протестированного кода.  
  
## <a name="prerequisites"></a>предварительные требования  
Если вы хотите использовать SSMA тестировщик, установите пакет расширения SSMA Sybase с **установки базы данных тест-инженер** включения параметра.  
  
Кроме того проверьте следующее.  
  
-   Поставщик OLE DB для Sybase устанавливается на компьютере, где [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] запускает.  
  
-   Общие интеграция Language Runtime (CLR) включена на [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] компонент Database Engine.  
  
Обратите внимание, что текущая версия SSMA тест-инженер не поддерживает параллельное выполнение разными пользователями на том же исходном или целевом сервере.  
  
## <a name="getting-started"></a>Приступая к работе  
[Создание тестовых случаев &#40;SybaseToSQL&#41;](../../ssma/sybase/creating-test-cases-sybasetosql.md)  
  
## <a name="see-also"></a>См. также  
[Установка компонентов SSMA на SQL Server &#40;SybaseToSQL&#41;](../../ssma/sybase/installing-ssma-components-on-sql-server-sybasetosql.md)  
[Параметры проекта &#40;преобразования&#41; &#40;SybaseToSQL&#41;](../../ssma/sybase/project-settings-conversion-sybasetosql.md)  
  
