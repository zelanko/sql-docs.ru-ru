---
title: Заметки о выпуске SQL Server 2019 | Документация Майкрософт
ms.date: 02/28/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: release-landing
ms.topic: article
ms.assetid: 13942af8-5a40-4cef-80f5-918386767a47
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: = sql-server-ver15 || = sqlallproducts-allversions
ms.openlocfilehash: 1afd1c7c1c3c142745e667662f51027218598e2f
ms.sourcegitcommit: 2533383a7baa03b62430018a006a339c0bd69af2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/01/2019
ms.locfileid: "57017730"
---
# <a name="sql-server-2019-preview-release-notes"></a>Заметки о выпуске предварительной версии SQL Server 2019
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В этой статье описываются ограничения и известные проблемы ознакомительной версии для сообщества (CTP) [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)]. Дополнительные сведения см. в следующих статьях:
- [Новые возможности в SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md)

> [!NOTE]
> Предварительные версии выпуска [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] публикуются для того, чтобы вы смогли опробовать возможности предстоящего выпуска. Они не являются поддерживаемыми или лицензированными для использования в рабочей среде. Явно не поддерживаются следующие сценарии.
>
> - Параллельная установка с другими версиями [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].
> - Обновление существующего экземпляра SQL Server с любой версии

**Попробуйте [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)].**
- [![Скачайте из Центра оценки](../includes/media/download2.png)](https://go.microsoft.com/fwlink/?LinkID=862101) [Скачайте [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] для установки на компьютерах с Windows](https://go.microsoft.com/fwlink/?LinkID=862101).
- Установите на компьютерах с Linux для [Red Hat Enterprise Server](../linux/quickstart-install-connect-red-hat.md), [SUSE Linux Enterprise Server](../linux/quickstart-install-connect-suse.md) и [Ubuntu](../linux/quickstart-install-connect-ubuntu.md).
- [Работайте с SQL Server 2019 в Docker](../linux/quickstart-install-connect-docker.md).

## <a name="ctp-23"></a>CTP 2.3
[!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP 2.3 — последний общедоступный выпуск [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)].

[!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP 2.3 доступен только в виде ознакомительной версии. Другие выпуски недоступны. Поддержка CTP 2.3 описана в файле `license_Eval.rtf` на установочном носителе.

Ограниченную поддержку можно найти в следующих ресурсах:

- Форумы
  - [Отзывы о SQL Server](https://aka.ms/sqlfeedback).
  - [Начало работы с SQL Server](https://social.msdn.microsoft.com/Forums/sqlserver/en-US/home?forum=sqlgetstarted).
  - [Transact-SQL](https://social.msdn.microsoft.com/Forums/sqlserver/en-US/home?forum=transactsql)
  - [Документация по SQL Server](https://social.msdn.microsoft.com/Forums/sqlserver/en-US/home?forum=sqldocumentation)

- Или опубликуйте твит [@SQLServer](https://twitter.com/SQLServer) с [#sqlhelp](https://twitter.com/search?q=%23sqlhelp).

### <a name="documentation-ctp-23"></a>Документация (CTP 2.3)

- **Проблема и последствия для клиентов**: Документация для SQL Server 2019 (15.x) ограничена, и материалы включены в набор документации по [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]. Содержимое статей, относящееся к SQL Server 2019 (15.x), отмечено с помощью раздела **Область применения**.

- **Проблема и последствия для клиентов.** Документация для [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] может быть отфильтрована по версии. Используйте элемент управления в верхней левой части каждой страницы документации для фильтрации в соответствии с вашими требованиями. 

- **Проблема и последствия для клиентов**: Локальные материалы для SQL Server 2019 (15.x) отсутствуют.

### <a name="hardware-and-software-requirements-ctp-23"></a>Требования к оборудованию и программному обеспечению (CTP 2.3)

- **Проблема и последствия для клиентов**: Требования к оборудованию и программному обеспечению по-прежнему проверяются и не являются окончательными для выпуска продукта.

  - **Оборудование**
    - [Windows — требования к процессору, памяти и операционной системе](../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md#pmosr).
    - [Linux — требования к системе](../linux/sql-server-linux-setup.md#system).
  - **Программное обеспечение**.
    - Windows Server 2016 или более поздней версии. Дополнительные требования см. в статье [Требования к оборудованию и программному обеспечению для установки SQL Server](../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md).
    - Платформа Microsoft .NET Framework 4.6.2. Доступна в [Центре загрузки](https://www.microsoft.com/download/details.aspx?id=53344).
    - Для Linux обратитесь к разделу [поддерживаемых платформ](../linux/sql-server-linux-setup.md#supportedplatforms).

### <a name="updated-compiler"></a>Обновленный компилятор

- **Проблема и последствия для клиентов**: сборка [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] выполнена с помощью обновленного компилятора. В CTP 2.1 была известная проблема, при которой результаты для чисел с плавающей точкой и результаты других сценариев преобразования могли отличаться от результатов таких же операций в прошлых версиях из-за использования обновленного компилятора. В CTP 2.2 была проведена дополнительная работа, чтобы убедиться, что сценарии, на которые распространяется эта проблема, возвращают те же результаты, что и в предыдущих версиях [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. На момент выхода CTP 2.3 эта проблема была полностью устранена. Если вы обнаружите какие-либо различия в результатах по сравнению с [!INCLUDE[ss2017](../includes/sssqlv14-md.md)], незамедлительно сообщите о них [команде разработчиков [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]](http://aka.ms/sqlfeedback).

- **Обходной путь**: Недоступно

- **Область применения**: SQL Server 2019 CTP 2.3, CTP 2.2, CTP 2.1

### <a name="utf-8-collations"></a>Параметры сортировки UTF-8

- **Проблема и последствия для клиентов**: Параметры сортировки с поддержкой UTF-8 не могут использоваться с некоторыми другими компонентами [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. UTF-8 не поддерживается при использовании следующих компонентов [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]:

  - Linked Server
  - Выполняющаяся в памяти OLTP
  - Внешняя таблица для PolyBase.

  > [!Note]
  > В настоящее время в пользовательском интерфейсе нет возможности выбрать параметры сортировки с поддержкой UTF-8 в Azure Data Studio или SQL Server Data Tools (SSDT). Последняя версия [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] (SSMS) поддерживает выбор параметров сортировки UTF-8 в пользовательском интерфейсе.
 
- **Обходной путь**: для CTP [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] — отсутствует.

- **Область применения**: [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP 2.3, CTP 2.2, CTP 2.1, CTP 2.0.

### <a name="sql-graph"></a>Граф SQL

- **Проблема и последствия для клиентов**: Средства, у которых есть зависимость от DacFx, например, средства импорта и экспорта, не будут работать с новыми функциями работы с графами, такими как ограничения ребер или синтаксис слияния языка DML. Написание скриптов в [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] может не работать.

- **Обходной путь**: Написание скриптов [!INCLUDE[tsql](../includes/tsql-md.md)] и их выполнение на сервере с помощью [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] или SQLCMD будет работать. Операции экспорта или импорта объектов базы данных, которые создают ограничения ребер, имеют новый синтаксис слияния языка DML или создают производные таблицы и представления для объектов графа, не будут работать. Пользователям придется вручную создавать такие объекты в своей базе данных с помощью скриптов [!INCLUDE[tsql](../includes/tsql-md.md)]. 

- **Область применения**: [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP 2.3, CTP 2.2, CTP 2.1, 2.0.

### <a name="always-encrypted-with-secure-enclaves"></a>Always Encrypted с безопасными анклавами.

- **Проблема и последствия для клиентов**: Для полнофункциональных вычислений будут выпущены несколько оптимизаций производительности, включая ограниченную функциональность (отсутствие индексирования и т. д.). Сейчас они отключены по умолчанию.

- **Обходной путь**: Чтобы включить полнофункциональные вычисления, выполните команду `DBCC traceon(127,-1)`. Дополнительные сведения см. в разделе [Настройка безопасного анклава](../relational-databases/security/encryption/configure-always-encrypted-enclaves.md#configure-a-secure-enclave).

- **Область применения**: [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP 2.3, 2.2, CTP 2.1, 2.0.

### <a name="system-dynamic-management-views"></a>Системные динамические административные представления

- **Проблема и последствия для клиентов**: Возвращающая табличные значения функция системы [sys.dm_db_objects_disabled_on_compatibility_level_change](../relational-databases/system-dynamic-management-views/spatial-data-sys-dm-db-objects-disabled-on-compatibility-level-change.md) возвращает случайные значения в столбце `dependency`.

- **Область применения**: [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP 2.3.

### <a name="sql-server-analysis-services-ssas"></a>Службы SQL Server Analysis Services (SSAS)

- **Проблема и последствия для клиентов**: В табличных моделях с динамической безопасностью в некоторых случаях пользователь видит данные другого пользователя, принадлежащего к той же роли.

  **Сценарий**. В модели есть по меньшей мере две роли. Одна из ролей не имеет какого-либо выражения динамической безопасности, которое бы содержало `USERNAME` или `USERPRINCIPALNAME`. Вторая роль с динамической безопасностью на уровне строк определяется для пользователей A и B с помощью выражения, содержащего `USERNAME` или `USERPRINCIPLENAME`. Пользователь А и пользователь Б могут подключаться к данным и запрашивать их, но при определенных обстоятельствах пользователь Б может видеть данные, которые предназначены только для пользователя A.

- **Обходной путь**: Добавьте фиктивную меру в модель. Например, `[DummyMeasure] := UserName()`. Это гарантирует, что динамические выражения оцениваются для выражений безопасности на уровне строк.

- **Область применения**: [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP 2.3.

[!INCLUDE[get-help-options-msft-only](../includes/paragraph-content/get-help-options.md)]

![MS_Logo_X-Small](../sql-server/media/ms-logo-x-small.png)
