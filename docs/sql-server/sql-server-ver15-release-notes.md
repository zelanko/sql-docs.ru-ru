---
title: Заметки о выпуске SQL Server 2019 | Документация Майкрософт
ms.date: 07/24/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: release-landing
ms.topic: article
ms.assetid: 13942af8-5a40-4cef-80f5-918386767a47
author: MikeRayMSFT
ms.author: mikeray
monikerRange: = sql-server-ver15 || = sqlallproducts-allversions
ms.openlocfilehash: a8e06fd47a8922e1b0ed494ce8ae47fc334ff8e6
ms.sourcegitcommit: 63c6f3758aaacb8b72462c2002282d3582460e0b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/25/2019
ms.locfileid: "68495489"
---
# <a name="sql-server-2019-preview-release-notes"></a>Заметки о выпуске предварительной версии SQL Server 2019
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В этой статье описываются ограничения и известные проблемы ознакомительной версии для сообщества (CTP) [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)]. Дополнительные сведения см. в следующих статьях:
- [Новые возможности в SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md)

## <a name="ctp-32"></a>CTP 3.2

[!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP 3.2 — последний общедоступный выпуск [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)].

[!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP 3.2 предоставляется только в качестве ознакомительного выпуска. Другие выпуски недоступны.

Подробные сведения о поддержке и лицензировании выпусков CTP приведены в файле `license_Eval.rtf` на установочном носителе.

[!INCLUDE[ctp-support-exclusion](../includes/ctp-support-exclusion.md)]

## <a name="documentation"></a>Документация

- **Проблема и последствия для клиентов**: Документация для SQL Server 2019 (15.x) ограничена, и материалы включены в набор документации по [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]. Содержимое статей, относящееся к SQL Server 2019 (15.x), отмечено с помощью раздела **Область применения**.

- **Проблема и последствия для клиентов.** Документация для [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] может быть отфильтрована по версии. Используйте элемент управления в верхней левой части каждой страницы документации для фильтрации в соответствии с вашими требованиями.

- **Проблема и последствия для клиентов**: Локальные материалы для SQL Server 2019 (15.x) отсутствуют.

## <a name="hardware-and-software-requirements"></a>Требования к оборудованию и программному обеспечению

- **Проблема и последствия для клиентов**: Требования к оборудованию и программному обеспечению по-прежнему проверяются и не являются окончательными для выпуска продукта.

  - **Оборудование**
    - [Windows — требования к процессору, памяти и операционной системе](../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md#pmosr).
    - [Linux — требования к системе](../linux/sql-server-linux-setup.md#system).
  - **Программное обеспечение**.
    - Windows Server 2016 или более поздней версии. Дополнительные требования см. в статье [Требования к оборудованию и программному обеспечению для установки SQL Server](../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md).
    - Платформа Microsoft .NET Framework 4.6.2. Доступна в [Центре загрузки](https://www.microsoft.com/download/details.aspx?id=53344).
    - Для Linux обратитесь к разделу [поддерживаемых платформ](../linux/sql-server-linux-setup.md#supportedplatforms).

## <a name = "release-notes"></a>Функции, исключенные из программы поддержки

- **Проблема и последствия для клиентов**: [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] исключает из программы поддержки следующие компоненты, функции и сценарии:
  - службы SQL Server Analysis Services
  - службы SQL Server Reporting Services
  - Группы доступности Always On в Kubernetes
  - Ускоренное восстановление баз данных.

- **Обходной путь**: Нет. Исключение применяется для всех клиентов, включая участников программы ранних последователей SQL.

- **Область применения**: Все выпуски CTP

## <a name="updated-compiler"></a>Обновленный компилятор

- **Проблема и последствия для клиентов**: сборка [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] выполнена с помощью обновленного компилятора. В CTP 2.1 была известная проблема, при которой результаты для чисел с плавающей точкой и результаты других сценариев преобразования могли отличаться от результатов таких же операций в прошлых версиях из-за использования обновленного компилятора. В CTP 2.2 была проведена дополнительная работа, чтобы убедиться, что сценарии, на которые распространяется эта проблема, возвращают те же результаты, что и в предыдущих версиях [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. На момент выхода CTP 3.2 эта проблема была полностью устранена. Если вы обнаружите какие-либо различия в результатах по сравнению с [!INCLUDE[ss2017](../includes/sssqlv14-md.md)], незамедлительно сообщите о них [команде разработчиков [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]](http://aka.ms/sqlfeedback).

- **Обходной путь**: Недоступно

- **Область применения**: Все выпуски CTP

## <a name="installation-wizard-may-wait-between-eula-pages"></a>Мастер установки может ожидать между страницами лицензионного соглашения

- **Проблема и последствия для клиентов**: При установке с помощью мастера установки процесс может слишком долго ожидать между лицензионным соглашением (EULA) для служб R Services и для Python.

- **Обходной путь**: Подождите, пока мастер установки продолжит работу. Время ожидания может превышать 30 минут.

- **Область применения**: SQL Server 2019 CTP 3.0

## <a name="utf-8-collations"></a>Параметры сортировки UTF-8

- **Проблема и последствия для клиентов**: Параметры сортировки с поддержкой UTF-8 не могут использоваться с некоторыми другими компонентами [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. UTF-8 не поддерживается при использовании следующих компонентов [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]:

  - Выполняющаяся в памяти OLTP
  - Внешняя таблица для PolyBase.
  - Always Encrypted

  > [!Note]
  > В настоящее время в пользовательском интерфейсе нет возможности выбрать параметры сортировки с поддержкой UTF-8 в Azure Data Studio или SQL Server Data Tools (SSDT). Последняя версия [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] (SSMS) 18 поддерживает выбор параметров сортировки UTF-8 в пользовательском интерфейсе.
 
- **Обходной путь**: для CTP [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] — отсутствует.

- **Область применения**: [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP 3.2, CTP 3.1, CTP 3.0, CTP 2.5, CTP 2.4, CTP 2.3, CTP 2.2, CTP 2.1, CTP 2.0.

## <a name="always-encrypted-with-secure-enclaves"></a>Always Encrypted с безопасными анклавами.

- **Проблема и последствия для клиентов**: Для полнофункциональных вычислений, которые сейчас они отключены по умолчанию, ожидаются оптимизации производительности и улучшения обработки ошибок.

- **Обходной путь**: Чтобы включить полнофункциональные вычисления, выполните команду `DBCC traceon(127,-1)`. См. подробнее о [включении полнофункциональных вычислений](../relational-databases/security/encryption/configure-always-encrypted-enclaves.md#configure-a-secure-enclave).

- **Область применения**: [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP 3.2, CTP 3.1

## <a name="sql-server-configuration-manager-may-not-start"></a>Диспетчер конфигурации SQL Server может не запуститься

- **Проблема и последствия для клиентов**: Диспетчер конфигурации SQL Server (SSCM) не запускается на компьютере без VCRuntime 140. При запуске SSCM может появиться следующее сообщение: 

  `
  MMC could not create the snap-in. The snap-in might not have been installed correctly.
  `

- **Обходной путь**:  Установите последнюю версию среды выполнения VC 2013 (x86):

  - [Verbose](https://support.microsoft.com/help/2977003/the-latest-supported-visual-c-downloads)
  - [Direct](https://support.microsoft.com/en-us/help/4032938/update-for-visual-c-2013-redistributable-package)

- **Область применения**: [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP 3.1, CTP 3.0, CTP 2.5.

[!INCLUDE[get-help-options-msft-only](../includes/paragraph-content/get-help-options.md)]

![MS_Logo_X-Small](../sql-server/media/ms-logo-x-small.png)
