---
title: "Установка Microsoft R Server из командной строки | Документация Майкрософт"
ms.custom: 
ms.date: 04/12/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fb4446ba-e9ce-4b93-9854-5e8a58507da0
caps.latest.revision: 4
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 811709fae77dee6daa46a97a51c44c02e372d9a8
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="install-microsoft-r-server-from-the-command-line"></a>Установка Microsoft R Server из командной строки
    
В этом разделе описывается использование командной строки SQL Server для установки Microsoft R Server в SQL Server 2016, или Установка Server обучения машины (изолированный) в 2017 г. SQL Server. 

> [!NOTE]
Можно также установить Microsoft R Server с помощью отдельного установщика Windows. Дополнительные сведения см. в разделе [установки R Server 9.0.1 для Windows](https://msdn.microsoft.com/microsoft-r/rserver-install-windows). 

## <a name="prerequisites"></a>Предварительные требования

Этот метод установки требуется знать о выполнении установки из командной строки SQL Server и знакомы с сценариев аргументов.

- Для**автоматической** установки требуется указать расположение программы установки и использовать аргументы, чтобы указать устанавливаемые компоненты. 
- Для **тихой** установки укажите те же самые аргументы, добавив параметр **/q** . При этом никакие запросы не выводятся и вмешательство пользователя не требуется. Однако при отсутствии любого из обязательных аргументов программа установки завершится ошибкой.

Дополнительные сведения см. в статье [Установка SQL Server 2016 из командной строки](../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md).

## <a name="sql-server-2017-microsoft-machine-learning-server-standalone"></a>SQL Server 2017 г: Корпорация Майкрософт машинного самообучения, Server (изолированный)

Выполните следующую команду из командной строки с повышенными привилегиями для установки только обучения машины Microsoft Server (изолированный) и его обязательные компоненты.  В примере показано аргументы, используемые для установки R.

```
Setup.exe /q /ACTION=Install /FEATURES=SQL_SHARED_MR, SQL_INST_MR  /IACCEPTROPENLICENSETERMS /IACCEPTSQLSERVERLICENSETERMS 
```

Чтобы просмотреть ход выполнения и запросы, удалите аргумент _/q_.

- **ФУНКЦИИ = SQL_SHARED_MR** возвращает только те компоненты сервера Machine обучения. Сюда входят все необходимые компоненты, которые автоматически устанавливаются по умолчанию.
- **SQL_INST_MR** необходим для поддержки installl языка R.
- **SQL_INST_MPY** требуется установить поддержку Python.
- **IACCEPTROPENLICENSETERMS** указывает, что вы приняли условия лицензионного соглашения для использования компонентов R с открытым исходным кодом.
- **IACCEPTPYTHONLICENSETERMS** указывает вы приняли условия лицензионного соглашения по использованию компонентов Python.
- **IACCEPTSQLSERVERLICENSETERMS** требуется для запуска мастера установки.

**Примечания**

1. Аргумент функции не требуется, — условия лицензии SQL Server.
2. Укажите хотя бы один язык, вместе с флагом лицензионного соглашения.
3. Можно установить один язык, или R и Python, но требуется отдельная лицензия для каждого.

## <a name="sql-server-2016-microsoft-r-server-standalone"></a>SQL Server 2016: Microsoft R Server (изолированный)

Выполните следующую команду из командной строки с повышенными привилегиями, чтобы установить только изолированный Microsoft R Server и его обязательные компоненты.  В этом примере аргументы, используемые программой установки SQL Server 2016.

```
Setup.exe /q /ACTION=Install /FEATURES=SQL_SHARED_MR /IACCEPTROPENLICENSETERMS /IACCEPTSQLSERVERLICENSETERMS
```

## <a name="offline-installation"></a>Автономная установка

При установке сервера Machine Learning или Microsoft R Server (изолированный) на компьютере, который имеет доступ к Интернету отсутствует, необходимо заранее загрузить необходимые компоненты R и скопируйте их в локальную папку. Расположения для скачивания см. в разделе [Установка компонентов R без доступа к Интернету](../r/installing-ml-components-without-internet-access.md).

## <a name="what-is-installed"></a>На устанавливаемые компоненты

После завершения установки можно просмотреть файл конфигурации, созданный программой установки SQL Server, а также сводку по действиям установки.

По умолчанию все сводные данные и журналы установки для SQL Server и связанные функции создаются в следующих папках:

- SQL Server 2016.`C:\Program Files\Microsoft SQL Server\130\Setup Bootstrap\Log`
- SQL Server 2017 г.:`C:\Program Files\Microsoft SQL Server\140\Setup Bootstrap\Log`

Для каждого устанавливаемого компонента создается отдельная вложенная папка.

Чтобы настроить другой экземпляр Microsoft R Server с теми же параметрами, можно повторно использовать файл конфигурации, созданный во время установки. Дополнительные сведения см. в статье [Установка SQL Server с помощью файла конфигурации](https://msdn.microsoft.com/library/dd239405.aspx)


## <a name="customize-your-r-environment"></a>Настройка среды R

После установки можно установить дополнительные пакеты R. Дополнительные сведения см. в разделе [Установка пакетов R и управление ими](../r/install-additional-r-packages-on-sql-server.md).

> [!IMPORTANT]
> Если вы собираетесь выполнять код R на сервере SQL Server, убедитесь, что установки те же пакеты на компьютере, который будет использоваться для разработки решения и экземпляр SQL Server для последующего выполнения либо развернуть решение.

После установки службы обучения машины для R (в базе данных), можно использовать отдельный установщик Windows для обновления версии R, который связан с определенным экземпляром SQL Server. Дополнительные сведения см. в разделе [SqlBindR используется для обновления R](../r/use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md).



