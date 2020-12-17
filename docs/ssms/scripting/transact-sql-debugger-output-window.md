---
title: Окно вывода
description: Узнайте, как использовать окно вывода для просмотра сообщений о состоянии и других выходных данных из отладчика SQL Server Management Studio и других средств.
titleSuffix: T-SQL Debugger
ms.prod: sql
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- Output Window [Transact-SQL]
- Output Window [SQL Server Management Studio]
ms.assetid: 9808e00c-c8f6-45cc-896e-192b8420f747
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 12/04/2019
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 66eda4d5c7cf3d5098eec0f00e4cb5dbf50cd0d7
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97478725"
---
# <a name="transact-sql-debugger---output-window"></a>Отладчик Transact-SQL, окно вывода

 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

В этом окне отображается сообщение о состоянии для различных функциональных возможностей в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Выходные данные доставляются в специальные панели окна **Вывод** из отладчика [!INCLUDE[tsql](../../includes/tsql-md.md)] , компонентов внешних средств или команд, выполняемых в **Окне команд** отладчика. Также доступны выходные данные внешних средств, таких как BAT и COM-файлы, обычно отображаемые в окне командной строки.

[!INCLUDE[ssms-old-versions](../../includes/ssms-old-versions.md)]
  
 **Получение доступа к окну «Вывод»**  
  
-   В меню **Вид** укажите пункт **Другие окна** и выберите **Вывод**.  
  
## <a name="options"></a>Параметры  
 **Список панелей вывода**  
 Отображает список панелей, доступных для просмотра. В зависимости от инструмента, использованного в окне **Вывод** , могут быть доступны несколько панелей данных для доставки пользователю сведений.  
  
 **Панель вывода**  
 Отображает вывод для панели, выбранной в **области-списке вывода**.  
  
## <a name="see-also"></a>См. также:  
 [Отладчик Transact-SQL](./transact-sql-debugger.md)