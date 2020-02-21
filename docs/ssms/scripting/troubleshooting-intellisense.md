---
title: Выявление проблем с технологией IntelliSense (SSMS)
description: Сведения об устранении неполадок и выявлении проблем с технологией IntelliSense с помощью SQL Server Management Studio (SSMS).
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.technology: scripting
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- unavailable options [IntelliSense]
- IntelliSense [SQL Server], troubleshooting
- IntelliSense [SQL Server], unavailable options
- troubleshooting [IntelliSense]
ms.assetid: 4b72ffc6-aea2-4e11-ab36-fa2de4d7bcc5
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: de4491bdeecdc635d12dca7cb0a51426524bdd67
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "75558686"
---
# <a name="identify-issues-with-intellisense---sql-server-management-studio-ssms"></a>Выявление проблем с технологией IntelliSense с помощью SQL Server Management Studio (SSMS)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  В некоторых случаях параметры технологии IntelliSense могут работать не так, как ожидается.  
  
## <a name="conditions-that-affect-intellisense"></a>Условия, влияющие на работу технологии IntelliSense  
 Следующие условия могут повлиять на работу технологии IntelliSense.  
  
-   Выше позиции курсора есть ошибка кода.  
  
     Если в коде выше текущей позиции ввода имеется незавершенная инструкция или другая ошибка, то технология IntelliSense может оказаться не в состоянии проанализировать элементы кода и поэтому работать не будет. Чтобы снова включить технологию IntelliSense, можно заключить соответствующий код в комментарий.  
  
-   Позиция ввода находится внутри комментария.  
  
     Параметры технологии IntelliSense недоступны в том случае, если позиция ввода находится в исходном файле внутри комментария.  
  
-   Позиция ввода находится внутри строкового литерала.  
  
     Параметры технологии IntelliSense недоступны в том случае, если позиция ввода находится внутри кавычек, содержащих строковый литерал, например:  
  
     `WHERE FirstName LIKE 'Patri%|'`  
  
-   Функции автоматизации отключены.  
  
     Многие функции технологии IntelliSense работают автоматически по умолчанию, но любую из них можно отключить.  
  
     Даже если автоматическое завершение инструкций отключено, то использование функции технологии IntelliSense возможно. Дополнительные сведения см. в статье [Настройка IntelliSense (среда SQL Server Management Studio)](../../relational-databases/scripting/configure-intellisense-sql-server-management-studio.md).  
  
## <a name="database-engine-query-intellisense"></a>Поддержка технологии IntelliSense в редакторе запросов к ядру СУБД  
 В отношении редактора запросов [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] действуют следующие ограничения.  
  
-   Функция IntelliSense в редакторе запросов [!INCLUDE[ssDE](../../includes/ssde-md.md)] поддерживает не все элементы синтаксиса языка [!INCLUDE[tsql](../../includes/tsql-md.md)] . Справка по параметрам не предоставляется по параметрам некоторых объектов, например расширенных хранимых процедур. Дополнительные сведения см. в разделе [Синтаксис языка Transact-SQL, поддерживаемый технологией IntelliSense](../../relational-databases/scripting/transact-sql-syntax-supported-by-intellisense.md).  
  
-   Технология Intellisense доступна только в случае, если редактор запросов компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] подключен к экземпляру [!INCLUDE[ssDE](../../includes/ssde-md.md)] версии [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] или более поздней версии. Технология Intellisense не доступна, когда редактор запросов подключен к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)]более ранней версии.  
  
-   Поддержка технологии IntelliSense отключается в редакторе запросов компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] при включении режима SQLCMD.  
  
-   Функциональность технологии IntelliSense не охватывает объекты базы данных, созданные в другом соединении, установленном после подключения окна редактора к базе данных. Если в функциях технологии IntelliSense отсутствуют такие объекты, как списки завершения, можно выбрать один из трех механизмов обновления кэша объектов для окна редактора.  
  
    -   В меню **Правка** выберите пункт **IntelliSense**, а затем пункт **Обновить локальный кэш**.  
  
    -   Используйте сочетание клавиш CTRL+SHIFT+R.  
  
    -   Отключите окно редактора от экземпляра компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] и установите соединение повторно.  
  
-   В списки завершения не включаются объекты базы данных, на которые нет разрешений. Ссылки на объекты, для которых есть разрешения, в технологии IntelliSense отмечаются флагами. Например, если открыть скрипт, написанный другим пользователем, все ссылки на объекты, для которых у другого пользователя есть разрешения, а у вас нет, отмечаются флагами как неверные.  
  
-   Списки завершения могут перестать функционировать при разрыве соединения с экземпляром компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)]. В этом случае необходимо восстановить соединение с экземпляром.  
  
  
