---
title: "Обновленные документы по службам Integration Services для SQL Server | Документы Майкрософт"
description: "Отрывки из недавно обновленного содержимого в документации по службам Integration Services для Microsoft SQL Server."
services: na
documentationcenter: 
author: MightyPen
manager: jhubbard
editor: 
ms.service: na
ms.topic: updart-autogen
ms.technology: database-engine
ms.custom: UpdArt.exe
ms.tgt_pltfrm: na
ms.devlang: na
ms.date: 12/02/2017
ms.author: genemi
ms.workload: integration-services
ms.openlocfilehash: 9660fa7239c14c3adc963cc75ceb98de8316734c
ms.sourcegitcommit: 29265ad41fbe3326c21c6908ec4275a3a38f1c09
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/04/2017
---
# <a name="new-and-recently-updated-integration-services-for-sql-server"></a>Новые и обновленные статьи по службам Integration Services для SQL Server



Почти каждый день корпорация Майкрософт вносит изменения в свои статьи на веб-сайте документации [Docs.Microsoft.com](http://docs.microsoft.com/). В этой статье приводятся отрывки из обновленных недавно статей, а также ссылки на новые статьи.

Статья создается программой и периодически обновляется. Отрывки из измененных статей могут иметь неидеальный формат или разметку исходной статьи. Картинки здесь не отображаются.

Последние обновления соответствуют следующему периоду времени и предметной области:



- *Диапазон дат обновлений:* &nbsp; **28.09.2017**&nbsp;–&nbsp;**02.12.2017**
- *Предметная область:* &nbsp; **Службы Integration Services для SQL Server**.




&nbsp;

## <a name="new-articles-created-recently"></a>Недавно созданные статьи

Приведенные ниже ссылки указывают на новые статьи, которые добавлены недавно.


1. [Хранение файлов в общих папках в локальной среде и в Azure и их извлечение](lift-shift/ssis-azure-files-file-shares.md)
2. [Проверка пакетов SSIS, развертываемых в Azure](lift-shift/ssis-azure-validate-packages.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Обновленные статьи с отрывками

В этом разделе приводятся отрывки из статей, в которые недавно внесены значительные изменения.

Отрывки отображаются отдельно от соответствующего семантического контекста. Кроме того, иногда фрагмент отделяется от синтаксиса разметки, окружающей саму статью. Таким образом, эти отрывки приводятся только для общего сведения. Они позволяют понять, стоит ли вам перейти по ссылке и прочитать всю статью полностью.

По этой и другим причинам не копируйте код из этих отрывков и не воспринимайте содержание этих отрывков как однозначно верное. Вместо этого пройдите по ссылке и ознакомьтесь с фактическим текстом статьи.





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>Сокращенный список недавно обновленных статей

В этом сокращенном списке приводятся ссылки на все обновленные статьи, перечисленные в разделе "Отрывки".

1. [Диспетчер подключений Hadoop](#TitleNum_1)
2. [Подключение к локальным источникам данных и общим папкам Azure с помощью проверки подлинности Windows](#TitleNum_2)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-hadoop-connection-managerconnection-managerhadoop-connection-managermd"></a>1. &nbsp;[Диспетчер подключений Hadoop](connection-manager/hadoop-connection-manager.md)

*Обновление: 28.11.2017* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Далее](#TitleNum_2))

<!-- Source markdown line 65.  ms.author= "douglasl".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 2d68f4e884304f1a28045b42b680c15cc6a41ec5 fb2429466ea4d545682975d8dbea47451ce98ec7  (PR=4113  ,  Filename=hadoop-connection-manager.md  ,  Dirpath=docs\integration-services\connection-manager\  ,  MergeCommitSha40=28cccac53767db70763e5e705b8cc59a83c77317) -->



**Подключение с использованием проверки подлинности Kerberos**

Чтобы использовать проверку подлинности Kerberos с диспетчером соединений Hadoop, локальную среду можно настроить двумя способами. Вы можете выбрать лучший вариант.
-   Вариант 1. [Подключение компьютера со службами SSIS к области Kerberos--#kerberos-join-realm).
-   Вариант 2. [Включение взаимного доверия между доменом Windows и областью Kerberos--#kerberos-mutual-trust).

**<a name="kerberos-join-realm"></a>Вариант 1. Подключение компьютера со службами SSIS к области Kerberos**


**Требования:**


-   Компьютер шлюза нужно подключить к области Kerberos. При этом он не должен подключаться к доменам Windows.

**Порядок настройки:**


**На компьютере со службами SSIS сделайте следующее:**

1.  Запустите служебную программу **Ksetup**, чтобы настроить сервер центра распространения ключей (KDC) и область Kerberos.

    Компьютер нужно настроить в качестве члена рабочей группы, так как область Kerberos отличается от домена Windows. Задайте область Kerberos и добавьте сервер KDC, как показано в примере ниже. При необходимости замените *REALM.COM* значением своей соответствующей области.

```
    C:> Ksetup /setdomain REALM.COM`
    C:> Ksetup /addkdc REALM.COM <your_kdc_server_address>
```

    Restart the computer after executing these two commands.

2.  Проверьте конфигурацию с помощью команды **Ksetup**. Выходные данные должны выглядеть так, как в следующем примере:

```
    C:> Ksetup
    default realm = REALM.COM (external)
    REALM.com:
        kdc = <your_kdc_server_address>
```

**<a name="kerberos-mutual-trust"></a>Вариант 2. Включение взаимного доверия между доменом Windows и областью Kerberos**


**Требования:**

-   Необходимо подключить компьютер шлюза к домену Windows.
-   Требуется разрешение на обновление параметров контроллера домена.

**Порядок настройки:**


> [!NOTE]
> При необходимости замените REALM.COM и AD.COM значениями своей соответствующей области и контроллера домена в следующем руководстве.



&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-connect-to-on-premises-data-sources-and-azure-file-shares-with-windows-authenticationlift-shiftssis-azure-connect-with-windows-authmd"></a>2. &nbsp;[Подключение к локальным источникам данных и общим папкам Azure с помощью проверки подлинности Windows](lift-shift/ssis-azure-connect-with-windows-auth.md)

*Обновлено: 27.11.2017* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Назад](#TitleNum_1))

<!-- Source markdown line 66.  ms.author= "douglasl".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 673386fca53cb60b983e0cb3cd4b9e2ee1dee0de 65458b4dceb92d01184c5e9c6f68ec0e8f16ba08  (PR=4104  ,  Filename=ssis-azure-connect-with-windows-auth.md  ,  Dirpath=docs\integration-services\lift-shift\  ,  MergeCommitSha40=19e1c4067142d33e8485cb903a7a9beb7d894015) -->



**Подключение к локальному серверу SQL Server**

Чтобы проверить возможность подключения к локальному серверу SQL Server, выполните указанные ниже действия.

1.  Чтобы выполнить эту проверку, найдите компьютер, не присоединенный к домену.

2.  На не присоединенном к домену компьютере выполните следующую команду, чтобы запустить среду SQL Server Management Studio (SSMS) с требуемыми учетными данными домена:

```
    runas.exe /netonly /user:<domain>\<username> SSMS.exe
```

3.  В среде SSMS проверьте возможность подключения к требуемому локальному серверу SQL Server.

**Подключение к локальной общей папке**

Чтобы проверить возможность подключения к локальной общей папке, выполните указанные ниже действия.

1.  Чтобы выполнить эту проверку, найдите компьютер, не присоединенный к домену.

2.  На компьютере, не присоединенном к домену, выполните приведенную ниже команду. Эта команда открывает окно командной строки с требуемыми учетными данными домена, а затем проверяет возможность подключения к общей папке, получая список каталогов.

```
    runas.exe /netonly /user:<domain>\<username> cmd.exe
    dir \\fileshare
```

3.  Проверьте, возвращен ли список каталогов из локальной общей папки, которую необходимо использовать.

**Подключение к общей папке на виртуальной машине Azure**

Чтобы подключиться к общей папке на виртуальной машине Azure, сделайте следующее:

1.  С помощью SQL Server Management Studio (SSMS) или другого средства подключитесь к базе данных SQL, в которой размещается база данных каталога SSIS (SSISDB).

2.  Откройте окно запроса для текущей базы данных SSISDB.

3.  Выполните хранимую процедуру `catalog.set_execution_credential`, как описано ниже.

```
    catalog.set_execution_credential @domain = N'.', @user = N'username of local account on Azure virtual machine', @password = N'password'
```

**Подключение к общей папке в службе файлов Azure**

Дополнительные сведения о файлах Azure см. в разделе [Файлы Azure](https://azure.microsoft.com/services/storage/files/).







## <a name="similar-articles"></a>Похожие статьи

<!--  HOW TO:
    Refresh this file's line items with the latest 'Count-in-Similars*' content.
    Then run Run-533-*.BAT
    2017-12-02  23:00pm
-->

Этот раздел содержит статьи, очень близкие к недавно измененным статьям из других предметных областей в общедоступном репозитории GitHub.com: [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/).

#### <a name="subject-areas-which-do-have-new-or-recently-updated-articles"></a>Предметные области, содержащие новые или недавно обновленные статьи

- [Новые + обновленные (3+14): **Углубленная аналитика для SQL**](../advanced-analytics/new-updated-advanced-analytics.md)
- [Новые + обновленные (1+0): **Analysis Services для SQL**](../analysis-services/new-updated-analysis-services.md)
- [Новые + обновленные (87+0): **Analytics Platform System для SQL**](../analytics-platform-system/new-updated-analytics-platform-system.md)
- [Новые + обновленные (5+4): **Подключение к SQL**](../connect/new-updated-connect.md)
- [Новые + обновленные (0+1): **Ядро СУБД для SQL**](../database-engine/new-updated-database-engine.md)
- [Новые + обновленные (2+2): **Integration Services для SQL**](../integration-services/new-updated-integration-services.md)
- [Новые + обновленные (10+9): **Linux для SQL**](../linux/new-updated-linux.md)
- [Новые + обновленные (2+4): **Реляционные базы данных для SQL**](../relational-databases/new-updated-relational-databases.md)
- [Новые + обновленные (4+2): **Reporting Services для SQL**](../reporting-services/new-updated-reporting-services.md)
- [Новые + обновленные (0+1): **примеры для SQL**](../sample/new-updated-sample.md)
- [Новые + обновленные (21+0): **SQL Operations Studio**](../sql-operations-studio/new-updated-sql-operations-studio.md)
- [Новые + обновленные(5+1): **Microsoft SQL Server**](../sql-server/new-updated-sql-server.md)
- [Новые + обновленные (0+1): **SQL Server Data Tools (SSDT)**](../ssdt/new-updated-ssdt.md)
- [Новые + обновленные (1+0): **Помощник по миграции SQL Server (SSMA)**](../ssma/new-updated-ssma.md)
- [Новые + обновленные (0+1): **SQL Server Management Studio (SSMS)**](../ssms/new-updated-ssms.md)
- [Новые + обновленные (0+2): **Transact-SQL**](../t-sql/new-updated-t-sql.md)

#### <a name="subject-areas-which-have-no-new-or-recently-updated-articles"></a>Предметные области, не содержащие новые или недавно обновленные статьи

- [Новые + обновленные (0+0): **Data Migration Assistant (DMA) для SQL**](../dma/new-updated-dma.md)
- [Новые + обновленные (0+0): **объекты данных ActiveX (ADO) для SQL**](../ado/new-updated-ado.md)
- [Новые + обновленные (0+0): **Data Quality Services для SQL**](../data-quality-services/new-updated-data-quality-services.md)
- [Новые + обновленные (0+0): **расширения интеллектуального анализа данных (DMX) для SQL**](../dmx/new-updated-dmx.md)
- [Новые + обновленные (0+0): документация **Master Data Services (MDS) для SQL**](../master-data-services/new-updated-master-data-services.md)
- [Новые + обновленные (0+0): **многомерные выражения (MDX) для SQL**](../mdx/new-updated-mdx.md)
- [Новые + обновленные (0+0): **ODBC (Open Database Connectivity) для SQL**](../odbc/new-updated-odbc.md)
- [Новые + обновленные (0+0): **PowerShell для SQL**](../powershell/new-updated-powershell.md)
- [Новые + обновленные (0+0): **Инструменты для SQL**](../tools/new-updated-tools.md)
- [Новые + обновленные (0+0): **XQuery для SQL**](../xquery/new-updated-xquery.md)


