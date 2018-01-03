---
title: "Тестирование перенесенные объекты базы данных (SybaseToSQL) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssma-sybase
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 4937f6b4-86bd-4070-88df-3d216306c33a
caps.latest.revision: "7"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2a20ba21c0e142db53579500cf7e9f87f15fa556
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
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
[Создание тестовых случаев &#40; SybaseToSQL &#41;](../../ssma/sybase/creating-test-cases-sybasetosql.md)  
  
## <a name="see-also"></a>См. также:  
[Установка компонентов SSMA на SQL Server &#40; SybaseToSQL &#41;](../../ssma/sybase/installing-ssma-components-on-sql-server-sybasetosql.md)  
[Параметры проекта &#40; Преобразование &#41; &#40; SybaseToSQL &#41;](../../ssma/sybase/project-settings-conversion-sybasetosql.md)  
  
