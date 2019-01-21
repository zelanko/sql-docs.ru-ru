---
title: Заметки о выпуске SQL Server 2019 | Документация Майкрософт
ms.date: 12/07/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: release-landing
ms.topic: article
ms.assetid: 13942af8-5a40-4cef-80f5-918386767a47
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: = sql-server-ver15 || = sqlallproducts-allversions
ms.openlocfilehash: 9d810c1a76eb4253c6d11abce7cd9992260c3708
ms.sourcegitcommit: 96032813f6bf1cba680b5e46d82ae1f0f2da3d11
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/15/2019
ms.locfileid: "54298951"
---
# <a name="sql-server-2019-preview-release-notes"></a>Заметки о выпуске предварительной версии SQL Server 2019

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

  > [!div class="nextstepaction"]
  > [Поделитесь своим мнением о содержании документации по SQL.](https://aka.ms/sqldocsurvey)

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

## <a name="ctp-22-december-2018"></a>CTP 2.2 (декабрь 2018 г.)
[!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP 2.2 — последний общедоступный выпуск [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)].

[!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP 2.2 доступен только в виде ознакомительной версии. Другие выпуски недоступны. Поддержка CTP 2.2 описана в файле `license_Eval.rtf` на установочном носителе.

Ограниченную поддержку можно найти в следующих ресурсах:

- Форумы
  - [Отзывы о SQL Server](https://aka.ms/sqlfeedback).
  - [Начало работы с SQL Server](https://social.msdn.microsoft.com/Forums/sqlserver/en-US/home?forum=sqlgetstarted).
  - [Transact-SQL](https://social.msdn.microsoft.com/Forums/sqlserver/en-US/home?forum=transactsql)
  - [Документация по SQL Server](https://social.msdn.microsoft.com/Forums/sqlserver/en-US/home?forum=sqldocumentation)

- Или опубликуйте твит [@SQLServer](https://twitter.com/SQLServer) с [#sqlhelp](https://twitter.com/search?q=%23sqlhelp).

### <a name="documentation-ctp-22"></a>Документация (CTP 2.2)

- **Проблема и последствия для клиентов**: Документация для SQL Server 2019 (15.x) ограничена, и материалы включены в набор документации по [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]. Содержимое статей, относящееся к SQL Server 2019 (15.x), отмечено с помощью раздела **Область применения**.

- **Проблема и последствия для клиентов.** Документация для [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] может быть отфильтрована по версии. Используйте элемент управления в верхней левой части каждой страницы документации для фильтрации в соответствии с вашими требованиями. 

- **Проблема и последствия для клиентов**: Локальные материалы для SQL Server 2019 (15.x) отсутствуют.

### <a name="hardware-and-software-requirements"></a>Требования к оборудованию и программному обеспечению

- **Проблема и последствия для клиентов**: Требования к оборудованию и программному обеспечению по-прежнему проверяются и не являются окончательными для выпуска продукта.

  - **Оборудование**
    - [Windows — требования к процессору, памяти и операционной системе](../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md#pmosr).
    - [Linux — требования к системе](../linux/sql-server-linux-setup.md#system).
  - **Программное обеспечение**.
    - Windows Server 2016 или более поздней версии. Дополнительные требования см. в статье [Требования к оборудованию и программному обеспечению для установки SQL Server](../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md).
    - Платформа Microsoft .NET Framework 4.6.2. Доступна в [Центре загрузки](https://www.microsoft.com/download/details.aspx?id=53344).
    - Для Linux обратитесь к разделу [поддерживаемых платформ](../linux/sql-server-linux-setup.md#supportedplatforms).

### <a name="updated-compiler"></a>Обновленный компилятор

- **Проблема и последствия для клиентов**: сборка [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] выполнена с помощью обновленного компилятора. В CTP 2.1 была известная проблема, при которой результаты для чисел с плавающей точкой и результаты других сценариев преобразования могли отличаться от результатов таких же операций в прошлых версиях из-за использования обновленного компилятора. В CTP 2.2 была проведена дополнительная работа, чтобы убедиться, что сценарии, на которые распространяется эта проблема, возвращают те же результаты, что и в предыдущих версиях [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. На момент выхода CTP 2.2 эта проблема была полностью устранена. Если вы обнаружите какие-либо различия в результатах по сравнению с [!INCLUDE[ss2017](../includes/sssqlv14-md.md)], незамедлительно сообщите о них [команде разработчиков [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]](http://aka.ms/sqlfeedback).

- **Обходной путь**: Недоступно

- **Область применения**: SQL Server 2019 CTP 2.2, CTP 2.1

### <a name="sql-server-integration-services-ssis-page-deployment-after-switching-db-to-single-user-mode-and-then-switching-back"></a>Развертывание пакета SQL Server Integration Services (SSIS) после переключения базы данных в однопользовательский режим и обратно

- **Проблема и последствия для клиентов**: После переключения SSISDB из однопользовательского режима обратно в многопользовательский при развертывании пакета может отображаться следующее сообщение об ошибке:

  `Cannot continue the execution because the session is in the kill state.`

- **Обходной путь**: Остановите и перезапустите экземпляр SQL Server, а затем переключите SSISDB обратно в многопользовательский режим.

- **Область применения**: SQL Server 2019 (предварительная версия) CTP 2.2, CTP 2.1

### <a name="utf-8-collations"></a>Параметры сортировки UTF-8

- **Проблема и последствия для клиентов**: Параметры сортировки с поддержкой UTF-8 не могут использоваться с некоторыми другими компонентами [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. UTF-8 не поддерживается при использовании следующих компонентов [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]:

  - Linked Server
  - Выполняющаяся в памяти OLTP
  - Внешняя таблица для PolyBase.

  > [!Note]
  > В настоящее время в пользовательском интерфейсе нет возможности выбрать параметры сортировки с поддержкой UTF-8 в Azure Data Studio или SQL Server Data Tools (SSDT). Последняя версия [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] (SSMS) поддерживает выбор параметров сортировки UTF-8 в пользовательском интерфейсе.
 
- **Обходной путь**: для CTP [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] — отсутствует.

- **Область применения**: [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP 2.2, CTP 2.1, CTP 2.0.

### <a name="sql-graph"></a>Граф SQL

- **Проблема и последствия для клиентов**: Средства, у которых есть зависимость от DacFx, например, средства импорта и экспорта, не будут работать с новыми функциями работы с графами, такими как ограничения ребер или синтаксис слияния языка DML. Написание скриптов в [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] может не работать.

- **Обходной путь**: Написание скриптов [!INCLUDE[tsql](../includes/tsql-md.md)] и их выполнение на сервере с помощью [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] или SQLCMD будет работать. Операции экспорта или импорта объектов базы данных, которые создают ограничения ребер, имеют новый синтаксис слияния языка DML или создают производные таблицы и представления для объектов графа, не будут работать. Пользователям придется вручную создавать такие объекты в своей базе данных с помощью скриптов [!INCLUDE[tsql](../includes/tsql-md.md)]. 

- **Область применения**: [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP 2.2, CTP 2.1, CTP 2.0.

### <a name="always-encrypted-with-secure-enclaves"></a>Always Encrypted с безопасными анклавами.

- **Проблема и последствия для клиентов**: Для полнофункциональных вычислений будут выпущены несколько оптимизаций производительности, включая ограниченную функциональность (отсутствие индексирования и т. д.). Сейчас они отключены по умолчанию.

- **Обходной путь**: Чтобы включить полнофункциональные вычисления, выполните команду `DBCC traceon(127,-1)`. Дополнительные сведения см. в разделе [Настройка безопасного анклава](../relational-databases/security/encryption/configure-always-encrypted-enclaves.md#configure-a-secure-enclave).

- **Область применения**: [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP 2.2, CTP 2.1, CTP 2.0.

## <a name="ctp-21-october-2018"></a>CTP 2.1 (октябрь 2018 г.)

[!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP 2.1 — предыдущий общедоступный выпуск [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)].

### <a name="udf-inlining"></a>Встроенные определяемые пользователем функции

- **Проблема и последствия для клиентов**: Существуют экстремальные сценарии, когда вложенные вызовы к встроенным функциям, определяемым пользователем, неправильно проходят проверку безопасности.
  
- **Обходной путь**: Отключите встраивание для таких определяемых пользователем функций с помощью параметра `INLINE = OFF`.

- **Область применения**: SQL Server 2019 CTP 2.1

### <a name="sql-server-integration-service---fuzzy-lookup-transformation"></a>Служба интеграции SQL Server — нечеткий уточняющий запрос

- **Проблема и последствия для клиентов**: Нечеткий уточняющий запрос, настроенный на повторное использование индекса, завершается следующей ошибкой:

  `The specified delimiters do not match the delimiters used to build the pre-existing match index "...". This error occurs when the delimiters used to tokenize fields do not match. This can have unknown effects on the matching behavior or results.`

- **Обходной путь**: Недоступно

- **Дополнительные сведения**: Недоступно  

- **Применимо к**: [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP2.1

### <a name="lightweight-query-profiling-infrastructure"></a>Упрощенная инфраструктура профилирования запросов

- **Проблема и последствия для клиентов**: В результате выполнения команды `ALTER DATABASE SCOPED CONFIGURATION SET LIGHTWEIGHT_QUERY_PROFILING = ON` возвращается синтаксическая ошибка. Сценарии, зависящие от выполнения этой команды, завершатся ошибкой.

  > [!NOTE]
  > В настоящее время упрощенной инфраструктурой профилирования запросов (LWP) нельзя управлять на уровне отдельной базы данных, и она остается активированной для всех баз данных по умолчанию. Дополнительные сведения о LWP см. в [статье о новых возможностях SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md).

- **Обходной путь**: для CTP [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] — отсутствует.

- **Область применения**: [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP 2.1 и CTP 2.0.

[!INCLUDE[get-help-options-msft-only](../includes/paragraph-content/get-help-options.md)]

![MS_Logo_X-Small](../sql-server/media/ms-logo-x-small.png)
