---
title: Заметки о выпуске SQL Server 2019 | Документация Майкрософт
ms.custom: ''
ms.date: 11/06/2018
ms.prod: sql-server-2018
ms.reviewer: ''
ms.technology:
- server-general
ms.topic: article
ms.assetid: 13942af8-5a40-4cef-80f5-918386767a47
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: = sql-server-ver15 || = sqlallproducts-allversions
ms.openlocfilehash: 7fba2c4989b6e50fe720a44e127b044dea93876d
ms.sourcegitcommit: a2be75158491535c9a59583c51890e3457dc75d6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2018
ms.locfileid: "51269807"
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
- [![Скачайте из Центра оценки](../includes/media/download2.png)](http://go.microsoft.com/fwlink/?LinkID=862101) [Скачайте [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] для установки на компьютерах с Windows](http://go.microsoft.com/fwlink/?LinkID=862101).
- Установите на компьютерах с Linux для [Red Hat Enterprise Server](../linux/quickstart-install-connect-red-hat.md), [SUSE Linux Enterprise Server](../linux/quickstart-install-connect-suse.md) и [Ubuntu](../linux/quickstart-install-connect-ubuntu.md).
- [Работайте с SQL Server 2019 в Docker](../linux/quickstart-install-connect-docker.md).

## <a name="ctp-21-november-2018"></a>CTP 2.1 (ноябрь 2018 г.)
[!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)]CTP 2.1 — последний общедоступный выпуск [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)].

[!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)]CTP 2.1 доступен только как выпуск Evaluation Edition. Другие выпуски недоступны. Поддержка CTP 2.1 описана в файле license_Eval.rtf на установочном носителе.

Ограниченную поддержку можно найти в следующих ресурсах:

- Форумы
  - [Отзывы о SQL Server](http://aka.ms/sqlfeedback).
  - [Начало работы с SQL Server](https://social.msdn.microsoft.com/Forums/sqlserver/en-US/home?forum=sqlgetstarted).
  - [Transact-SQL](https://social.msdn.microsoft.com/Forums/sqlserver/en-US/home?forum=transactsql)
  - [Документация по SQL Server](https://social.msdn.microsoft.com/Forums/sqlserver/en-US/home?forum=sqldocumentation)

- Или опубликуйте твит [@SQLServer](http://twitter.com/SQLServer) с [#sqlhelp](https://twitter.com/search?q=%23sqlhelp).

### <a name="documentation-ctp-21"></a>Документация (CTP 2.1)

- **Проблема и последствия для клиентов.** Документация для SQL Server 2019 (15.x) ограничена, и материалы включены в набор документации по [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]. Содержимое статей, относящееся к SQL Server 2019 (15.x), отмечено с помощью раздела **Область применения**.

- **Проблема и последствия для клиентов.** Документация для [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] может быть отфильтрована по версии. Используйте элемент управления в верхней левой части каждой страницы документации для фильтрации в соответствии с вашими требованиями. 

- **Проблема и последствия для клиентов.** Локальные материалы для SQL Server 2019 (15.x) отсутствуют.

### <a name="hardware-and-software-requirements"></a>Требования к оборудованию и программному обеспечению

- **Проблема и последствия для клиентов.** Требования к оборудованию и программному обеспечению по-прежнему проверяются и не являются окончательными для выпуска продукта.

  - **Оборудование**
    - [Windows — требования к процессору, памяти и операционной системе](../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md#pmosr).
    - [Linux — требования к системе](../linux/sql-server-linux-setup.md#system).
  - **Программное обеспечение**.
    - Windows Server 2016 или более поздней версии. Дополнительные требования см. в статье [Требования к оборудованию и программному обеспечению для установки SQL Server](../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md).
    - Платформа Microsoft .NET Framework 4.6.2. Доступна в [Центре загрузки](http://www.microsoft.com/download/details.aspx?id=53344).
    - Для Linux обратитесь к разделу [поддерживаемых платформ](../linux/sql-server-linux-setup.md#supportedplatforms).

### <a name="floating-point-results"></a>Результаты с плавающей запятой

- **Проблема и последствия для клиентов.** В предварительной версии SQL Server 2019 используется обновленный компилятор для сборки SQL Server. В некоторых случаях код, скомпилированный с помощью нового компилятора, может возвращать значения с плавающей запятой, которые отличаются от значений в предыдущих версиях SQL Server. Изменение в поведении будет ограничено новым уровнем совместимости (150) в будущей ознакомительной версии для сообщества.

- **Обходное решение.** Н/Д.

- **Область применения.** SQL Server 2019 CTP 2.1.

### <a name="sql-server-integration-services-ssis-page-deployment-after-switching-db-to-single-user-mode-and-then-switching-back"></a>Развертывание пакета SQL Server Integration Services (SSIS) после переключения базы данных в однопользовательский режим и обратно

- **Проблема и последствия для клиентов.** После переключения SSISB из однопользовательского режима назад в многопользовательский при развертывании пакета может отображаться следующее сообщение об ошибке:

  `Cannot continue the execution because the session is in the kill state.`

- **Обходное решение.** Остановите и перезапустите экземпляр SQL Server, а затем переключите SSISDB назад в многопользовательский режим. 

- **Область применения.** SQL Server 2019 (предварительная версия) CTP 2.1.


### <a name="udf-inlining"></a>Встроенные определяемые пользователем функции 

- **Проблема и последствия для клиентов.** Существуют редкие сценарии, когда вложенные вызовы к встроенным функциям, определяемым пользователем, неправильно проходят проверку безопасности.
  
- **Обходное решение.** Отключите встраивание для таких определяемых пользователем функций с помощью параметра `INLINE = OFF`.

- **Область применения.** SQL Server 2019 CTP 2.1.

### <a name="lightweight-query-profiling-infrastructure"></a>Упрощенная инфраструктура профилирования запросов

- **Проблема и последствия для клиентов.** В результате выполнения команды `ALTER DATABASE SCOPED CONFIGURATION SET LIGHTWEIGHT_QUERY_PROFILING = ON` возвращается синтаксическая ошибка. Сценарии, зависящие от выполнения этой команды, завершатся ошибкой.

  > [!NOTE]
  > В настоящее время упрощенной инфраструктурой профилирования запросов (LWP) нельзя управлять на уровне отдельной базы данных, и она остается активированной для всех баз данных по умолчанию. Дополнительные сведения о LWP см. в [статье о новых возможностях SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md).

- **Обходное решение.** Для [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP — отсутствует.

- **Область применения.** [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP 2.1 и CTP 2.0.

### <a name="utf-8-collations"></a>Параметры сортировки UTF-8

- **Проблема и последствия для клиентов.** Параметры сортировки с поддержкой UTF-8 не могут использоваться с некоторым другими компонентами [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. UTF-8 не поддерживается при использовании следующих компонентов [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]:

  - Репликация SQL Server
  - Linked Server
  - Выполняющаяся в памяти OLTP
  - Внешняя таблица для PolyBase.

    Также обратите внимание, что в настоящее время в пользовательском интерфейсе нет возможности выбрать параметры сортировки с поддержкой UTF-8 в Azure Data Studio или SSDT. Последняя версия SSMS поддерживает выбор параметров сортировки UTF-8 в пользовательском интерфейсе.

- **Обходное решение.** Для [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP — отсутствует.

- **Область применения.** [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP 2.1, CTP 2.0.

### <a name="sql-graph"></a>Граф SQL

- **Проблема и последствия для клиентов.** Средства, у которых есть зависимость от DacFx, например средства импорта и экспорта, не будут работать с новыми функциями работы с графами, такими как ограничения ребер или синтаксис слияния языка DML. Написание скриптов в [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] может не работать.

- **Обходное решение.** Написание скриптов [!INCLUDE[tsql](../includes/tsql-md.md)] и их выполнение на сервере с помощью [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] или SQLCMD будет работать. Операции экспорта или импорта объектов базы данных, которые создают ограничения ребер, имеют новый синтаксис слияния языка DML или создают производные таблицы и представления для объектов графа, не будут работать. Пользователям придется вручную создавать такие объекты в своей базе данных с помощью скриптов [!INCLUDE[tsql](../includes/tsql-md.md)]. 

- **Область применения.** [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP 2.1, 2.0.

### <a name="always-encrypted-with-secure-enclaves"></a>Always Encrypted с безопасными анклавами

- **Проблема и последствия для клиентов.** Для полнофункциональных вычислений будут выпущены несколько оптимизаций производительности, включая ограниченную функциональность (отсутствие индексирования и т. д.). Сейчас они отключены по умолчанию.

- **Обходное решение.** Чтобы включить полнофункциональные вычисления, запустите `DBCC traceon(127,-1)`. Дополнительные сведения см. в разделе [Настройка безопасного анклава](../relational-databases/security/encryption/configure-always-encrypted-enclaves.md#configure-a-secure-enclave).

- **Область применения.** [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP 2.1, 2.0.

### <a name="sql-server-integration-service---fuzzy-lookup-transformation"></a>Служба интеграции SQL Server — нечеткий уточняющий запрос

- **Проблема и последствия для клиентов.** Нечеткий уточняющий запрос, настроенный на повторное использование индекса, завершается следующей ошибкой:

  `The specified delimiters do not match the delimiters used to build the pre-existing match index "...". This error occurs when the delimiters used to tokenize fields do not match. This can have unknown effects on the matching behavior or results.`

- **Обходное решение.** Н/Д.

- **Дополнительные сведения.** Н/Д  

- **Область применения.** [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP2.1

## <a name="ctp-20-september-2018"></a>CTP 2.0 (сентябрь 2018 г.)

[!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP 2.0 — это первый общедоступный выпуск [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)].

### <a name="sql-server-integration-services-ssis-transfer-database-task"></a>Задача "Передача базы данных" SQL Server Integration Services (SSIS)

- **Проблема и последствия для клиентов.** При настройке `Transfer Database Task` для передачи базы данных в режиме `Database Online` может произойти сбой примерно со следующей ошибкой:

  >Метод Execute в задаче возвратил код ошибки 0x80131500 (ошибка при передаче данных; подробнее см. в описании внутреннего исключения). Метод Execute должен завершиться успешно и показать результат, используя параметр "out".

- **Обходное решение.** Выполните `DBCC TRACEON (7416,-1)` на сервере и повторите попытку.

- **Область применения**: [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP 2.0.

[!INCLUDE[get-help-options-msft-only](../includes/paragraph-content/get-help-options.md)]

![MS_Logo_X-Small](../sql-server/media/ms-logo-x-small.png)
