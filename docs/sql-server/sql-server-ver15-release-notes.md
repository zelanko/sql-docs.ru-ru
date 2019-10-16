---
title: Заметки о выпуске SQL Server 2019 | Документация Майкрософт
ms.date: 10/07/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: release-landing
ms.topic: article
ms.assetid: 13942af8-5a40-4cef-80f5-918386767a47
author: MikeRayMSFT
ms.author: mikeray
monikerRange: = sql-server-ver15 || = sqlallproducts-allversions
ms.openlocfilehash: 9b6895abfa0b09459911eba03b52837379f2d162
ms.sourcegitcommit: 512acc178ec33b1f0403b5b3fd90e44dbf234327
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/08/2019
ms.locfileid: "72041187"
---
# <a name="sql-server-2019-preview-release-notes"></a>Заметки о выпуске предварительной версии SQL Server 2019
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В статье описаны ограничения и известные проблемы, связанные с [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)]. Дополнительные сведения см. в следующих статьях:

>[Новые возможности в SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md)

>[!NOTE]
>Содержимое публикуется для релиз-кандидата [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]. Релиз-кандидат — это предварительная версия программного обеспечения. Информация может быть изменена. Дополнительные сведения о сценариях поддержки см. в разделе о [поддержке](#support).

## <a name="includesql-server-2019includessssqlv15-mdmd-release-candidate-rc"></a>Релиз-кандидат [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]

Релиз-кандидат [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] — это последний общедоступный выпуск [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)].

Релиз-кандидат [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] предоставляется только в качестве ознакомительного выпуска. Другие выпуски недоступны.

Подробные сведения о поддержке и лицензировании релиз-кандидатов программного обеспечения см. в файле `license_Eval.rtf` на установочном носителе.

[!INCLUDE[ctp-support-exclusion](../includes/ctp-support-exclusion.md)]

## <a name="documentation"></a>Документация

- **Проблема и последствия для клиентов**: Документация для SQL Server 2019 (15.x) ограничена, и материалы включены в набор документации по [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]. Содержимое статей, относящееся к SQL Server 2019 (15.x), отмечено с помощью раздела **Область применения**.

- **Проблема и последствия для клиентов.** Документация для [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] может быть отфильтрована по версии. Используйте элемент управления в верхней левой части каждой страницы документации для фильтрации в соответствии с вашими требованиями.

- **Проблема и последствия для клиентов**: Локальные материалы для SQL Server 2019 (15.x) отсутствуют.

## <a name="build-number"></a>Номер сборки

Номер сборки для SQL Server 2019 RC в Windows, Linux и контейнерах — `15.0.1900.25`.  Номер сборки для SQL Server 2019 RC в кластерах больших данных — `15.0.1900.47`.

## <a name="hardware-and-software-requirements"></a>Требования к оборудованию и программному обеспечению

- **Проблема и последствия для клиентов**: Требования к оборудованию и программному обеспечению по-прежнему проверяются и не являются окончательными для выпуска продукта.

  - **Оборудование**
    - [Windows — требования к процессору, памяти и операционной системе](../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md#pmosr).
    - [Linux — требования к системе](../linux/sql-server-linux-setup.md#system).
  - **Программное обеспечение**.
    - Windows Server 2016 или более поздней версии. Дополнительные требования см. в статье [Требования к оборудованию и программному обеспечению для установки SQL Server](../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md).
    - Платформа Microsoft .NET Framework 4.6.2. Доступна в [Центре загрузки](https://www.microsoft.com/download/details.aspx?id=53344).
    - Для Linux обратитесь к разделу [поддерживаемых платформ](../linux/sql-server-linux-setup.md#supportedplatforms).

## <a name="sql-server-installation-may-fail-if-ssms-18x-is-installed"></a>Установка SQL Server может быть прервана, если установлена среда SSMS 18.x.

- **Проблема и последствия для клиентов**: при установке [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] происходит сбой, если следующие установки выполняются в приведенном ниже порядке:
  1. SQL Server Management Studio (SSMS) версии 18.0, 18.1, 18.2 или 18.3 установлена на сервере.
  1. Предпринята попытка установки [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] со съемного носителя. Например, с установочного носителя DVD.

- **Обходной путь**:
  1. Удалите любую версию SSMS выше, чем SSMS 18.3.1.
  1. Установите более новую версию SSMS (18.3.1 или новее). Для получения последней версии обратитесь к статье [Скачивание SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md).
  1. Установите [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] как обычно.

  >[!NOTE]
  >Требуется удаление.

- **Область применения**: релиз-кандидат [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)].

## <a name="updated-compiler"></a>Обновленный компилятор

- **Проблема и последствия для клиентов**: сборка [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] выполнена с помощью обновленного компилятора. В CTP 2.1 была известная проблема, при которой результаты для чисел с плавающей точкой и результаты других сценариев преобразования могли отличаться от результатов таких же операций в прошлых версиях из-за использования обновленного компилятора. В CTP 2.2 была проведена дополнительная работа, чтобы убедиться, что сценарии, на которые распространяется эта проблема, возвращают те же результаты, что и в предыдущих версиях [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. На момент выхода релиз-кандидата проблемы устранены. Если вы обнаружите какие-либо различия в результатах по сравнению с [!INCLUDE[ss2017](../includes/sssqlv14-md.md)], незамедлительно сообщите о них [команде разработчиков [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]](https://aka.ms/sqlfeedback).

- **Обходной путь**: Недоступно

- **Область применения**: релиз-кандидат.

## <a name="installation-wizard-may-wait-between-eula-pages"></a>Мастер установки может ожидать между страницами лицензионного соглашения

- **Проблема и последствия для клиентов**: При установке с помощью мастера установки пауза между отображением лицензионных соглашений (EULA) для служб R Services и Python может затянуться.

- **Обходной путь**: Подождите, пока мастер установки продолжит работу. Время ожидания может превышать 30 минут.

- **Область применения**: [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP 3.0

## <a name="utf-8-collations"></a>Параметры сортировки UTF-8

- **Проблема и последствия для клиентов**: Параметры сортировки с поддержкой UTF-8 не могут использоваться с некоторыми другими компонентами [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. UTF-8 не поддерживается при использовании следующих компонентов [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]:

  - Выполняющаяся в памяти OLTP
  - Внешняя таблица для PolyBase (релиз-кандидат 1 [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)])
  - Always Encrypted (в версиях, предшествующих релиз-кандидату 1 [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)])
  - Связанные серверы (в версиях, предшествующих CTP 3.2 [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)])

  > [!Note]
  > В настоящее время в пользовательском интерфейсе нет возможности выбрать параметры сортировки с поддержкой UTF-8 в Azure Data Studio или SQL Server Data Tools (SSDT). Последняя версия [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] (SSMS) 18 поддерживает выбор параметров сортировки UTF-8 в пользовательском интерфейсе.
 
- **Обходной путь**: для CTP [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] — отсутствует.


- **Область применения**: все выпуски CTP.

## <a name="always-encrypted-with-secure-enclaves"></a>Always Encrypted с безопасными анклавами.

- **Проблема и последствия для клиентов**: Для полнофункциональных вычислений, которые сейчас они отключены по умолчанию, ожидаются оптимизации производительности и улучшения обработки ошибок.

- **Обходной путь**: Чтобы включить полнофункциональные вычисления, выполните команду `DBCC traceon(127,-1)`. См. подробнее о [включении полнофункциональных вычислений](../relational-databases/security/encryption/configure-always-encrypted-enclaves.md#configure-a-secure-enclave).

- **Область применения**: [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP 3.2, CTP 3.1

## <a name="sql-server-configuration-manager-may-not-start"></a>Диспетчер конфигурации SQL Server может не запуститься

- **Проблема и последствия для клиентов**: Диспетчер конфигурации SQL Server (SSCM) не запускается на компьютере без VCRuntime 140 (VCRUNTIME140.dll). При запуске SSCM может появиться следующее сообщение: 


  `MMC could not create the snap-in. The snap-in might not have been installed correctly.`

- **Обходной путь**:  Установите последнюю версию среды выполнения VC 2013 (x86):

  - [Verbose](https://support.microsoft.com/help/2977003/the-latest-supported-visual-c-downloads)
  - [Direct](https://support.microsoft.com/help/4032938/update-for-visual-c-2013-redistributable-package)

- **Область применения**: [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP 3.1, CTP 3.0, CTP 2.5.

## <a name="always-on-availability-group-kubernetes-operator-not-supported"></a>Оператор Kubernetes для групп доступности Always On не поддерживается.

- **Проблема и последствия для клиентов**: Оператор Kubernetes для групп доступности Always On не поддерживается в этом релиз-кандидате и будет недоступен в RTM-версии. 

- **Обходной путь**: None

- **Область применения**: релиз-кандидат [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)].

## <a name="master-data-service-notification-email-contains-broken-link"></a>Уведомление от службы Master Data Services по электронной почте содержит неработающую ссылку

- **Проблема и последствия для клиентов**: Сообщение электронной почты с уведомлением от службы Master Data Services (MDS) содержит неработающую ссылку. Ссылка ведет на страницу, которая возвращает сообщение об ошибке наподобие следующего:

   `The view 'Index' or its master was not found or no view engine supports the searched locations.`

- **Обходной путь**: Откройте портал MDS и перейдите к ресурсу вручную.

- **Область применения**: релиз-кандидат SQL Server 2019.

## <a name="machine-learning-services"></a>Службы машинного обучения

Сведения о проблемах в Службах машинного обучения SQL Server см. в статье [Known issues in SQL Server Machine Learning Services](../advanced-analytics/known-issues-for-sql-server-machine-learning-services.md) (Известные проблемы в Службах машинного обучения SQL Server).

[!INCLUDE[get-help-options-msft-only](../includes/paragraph-content/get-help-options.md)]

![MS_Logo_X-Small](../sql-server/media/ms-logo-x-small.png)
