---
title: "Подготовьте виртуальную машину для машинного обучения в Azure | Документы Microsoft"
ms.custom: 
ms.date: 10/31/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c8826df7-aa67-4768-baa9-bdc875c4a766
caps.latest.revision: 
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.openlocfilehash: 781622d51b7112d3a501652b7c320ab27e74ae35
ms.sourcegitcommit: c77a8ac1ab372927c09bf241d486e96881b61ac9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/29/2018
---
# <a name="provision-a-virtual-machine-for-machine-learning-on-azure"></a>Подготовьте виртуальную машину для машинного обучения в Azure

Виртуальные машины в Azure — это возможность быстро настроить полный серверной среде для машинного обучения решения.

В этой статье перечислены образы виртуальных машин, которые содержат SQL Server с помощью машинного обучения, а также некоторые связанные виртуальные машины.

Также ответы на часто задаваемые вопросы об изменении или обновлении существующего экземпляра SQL Server на виртуальной машине.

+ [Список текущего виртуальных машин](#bkmk_list)

## <a name="provision-a-virtual-machine-with-sql-server-and-machine-learning"></a>Подготовьте виртуальную машину с SQL Server и машинное обучение

Если вы не знакомы с помощью виртуальных машинах Azure, мы рекомендуем, отображается в следующих статьях, Дополнительные сведения об использовании портала и настройка виртуальной машины.

+ [Виртуальные машины — приступая к работе](https://azure.microsoft.com/documentation/learning-paths/virtual-machines/)
+ [Приступая к работе с виртуальными машинами Windows](https://azure.microsoft.com/documentation/articles/virtual-machines-windows-hero-tutorial/)

Убедитесь, что для использования новой версии портала Azure или Azure Marketplace. Некоторые рисунки недоступны при просмотре коллекции на классическом портале Azure.

**Создание виртуальной машины**

1. Откройте портал Azure: [portal.azure.com](https:portal.azure.com).

2. Нажмите кнопку **виртуальные машины**, или нажмите кнопку **New**.

3. Нажмите кнопку **Добавить**.

4. В поле поиска в верхней части страницы введите «Server машины обучения» или «SQL Server» для просмотра списка связанных виртуальных машин.

5. Ознакомьтесь с требованиями и нажмите кнопку **создать** Чтобы приступить к работе.

6. Виртуальная машина будет создана и запущена, нажмите кнопку **Connect** кнопку, чтобы открыть соединение и войдите в систему на новом компьютере.

5. После подключения можно установить дополнительные пакеты R или Python, или настроить средстве предпочтительный разработки.

### <a name="connect-to-the-virtual-machine"></a>Подключитесь к виртуальной машине

Способ, когда клиент подключается к SQL Server, работающий на виртуальной машине зависит от расположения клиента и конфигурации сети.

Дополнительные сведения см. в разделе [подключение к виртуальной машине SQL Server в Azure](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-sql-connect).

## <a name="frequently-asked-questions"></a>Часто задаваемые вопросы

Этот раздел содержит некоторые распространенные вопросы о машинного обучения виртуальных машин от корпорации Майкрософт.

### <a name="can-i-install-a-virtual-machine-with-sql-server-2017"></a>Можно установить виртуальную машину с SQL Server 2017 г.

Виртуальную машину под управлением Windows для SQL Server 2017 г Enterprise Edition, включающий службы обучения машины доступен, начиная с ноября 2017 г. 

Для объявления о новых виртуальных машин обработки и анализа данных просмотрите эти сайты блога:

+ [Cortana аналитики и машинное обучение](https://blogs.technet.microsoft.com/machinelearning/)
+ [Инсайдера разработки платформы данных](https://blogs.technet.microsoft.com/dataplatforminsider/)

### <a name="adding-sql-server-to-an-existing-virtual-machine"></a>Добавление существующей виртуальной машины SQL Server

Помимо создания виртуальной машины с помощью образа, уже существует на компьютере с SQL Server обучения, можно установить SQL Server на основе существующей виртуальной машины и включение машинного обучения функции. Рекомендуется использовать выпуск Enterprise или Developer, чтобы избежать ограничения ресурсов. Также необходимо использовать лицензионный ключ.

При запуске программы установки, не забудьте установить машинного обучения компонентов и хотя бы один язык (R или Python). Некоторые дополнительные действия, необходимые для включения службы обучения машины, для взаимодействия с SQL Server, а также включение сети на виртуальной машине.

Дополнительные сведения см. в разделе [Установка служб SQL Server R на виртуальной машине Azure](../r/installing-sql-server-r-services-on-an-azure-virtual-machine.md).

### <a name="using-machine-learning-in-azure-sql-database"></a>С помощью машинного обучения в базе данных Azure SQL

В настоящее время для текущих разработках приостанавливается на предварительную версию поддержки R в Azure SQL. Дополнительные сведения см. в разделе [базу данных SQL Azure](../r/using-r-in-azure-sql-database.md).

### <a name="can-i-upgrade-the-sql-server-version-on-a-virtual-machine"></a>Можно обновить версии SQL Server на виртуальной машине?

Несмотря на то, что образы SQL Server 2016 поддерживает R, если вы хотите использовать Python, можно обновить до SQL Server 2017 г., который также обновляет других машинного обучения компонентов.

Чтобы обновить версию SQL Server, установленный, откройте Центр установки SQL Server на виртуальной машине и выберите **обновление** параметр. В зависимости от виртуальной машины был создан, лицензии могут быть необходимы.

Дополнительные сведения см. в разделе [обновление SQL Server с помощью мастера установки](https://docs.microsoft.com/sql/database-engine/install-windows/upgrade-sql-server-using-the-installation-wizard-setup).

### <a name="can-i-upgrade-just-the-machine-learning-components"></a>Можно обновить только машинного обучения компоненты?

При публикации новых обновлений для RevoScaleR, MicrosoftML или revoscalepy, можно обновить машинного обучения компонентов, используемых SQL Server, с помощью процесса, известного как _привязки_. При этом не меняется вашей версии SQL Server, но это приводит к изменению политика поддержки для экземпляра.

Дополнительные сведения см. в разделе [SqlBindR используется для обновления компонентов обучения машины на сервере SQL Server](../r/use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md).

### <a name="how-do-i-access-data-in-an-azure-storage-account"></a>Как получить доступ к данным в учетной записи хранения Azure?

Если вам нужно использовать данные из своей учетной записи хранения Azure, существует несколько вариантов доступа к данным или их перемещения:

+ Скопируйте данные из вашей учетной записи хранения в локальную файловую систему с помощью служебной программы, например [AzCopy](https://azure.microsoft.com/documentation/articles/storage-use-azcopy/#copy-files-in-azure-file-storage-with-azcopy-preview-version-only). 

+ Добавьте файлы в общую папку в вашей учетной записи хранения и затем подключите ее как сетевой диск в виртуальной машине. Дополнительные сведения см. в разделе [Mounting Azure files](https://azure.microsoft.com/documentation/articles/storage-dotnet-how-to-use-files/)(Подключение файлов Azure). 

### <a name="how-do-i-use-data-from-azure-data-lake-storage-adls"></a>Как использовать данные из хранилища Azure Data Lake (ADLS)?

Можно считывать данные из хранилища ADLS, с помощью RevoScaleR, с помощью webHDFS для ссылки на учетную запись хранения, таким же образом HDFS файловой системы. Дополнительные сведения см. в разделе этой статьи: [с помощью R для выполнения операций файловой системы в хранилище Озера данных Azure](https://blogs.msdn.microsoft.com/microsoftrservertigerteam/2017/03/14/using-r-to-perform-filesystem-operations-on-azure-data-lake-store/).

### <a name="i-cant-find-the-rre-virtual-machine"></a>Не удается найти RRE виртуальной машины

«RRE для виртуальной машины Windows», существовавшей ранее в Azure Marketplace будет заменен изображения «Машины обучения сервера для Windows».

Образов сервера обучения компьютера также доступны для версии Linux CentOS 7.2, версии Linux RedHat 7.2 и Ubuntu версии 16.04.

Дополнительные сведения см. в разделе [сервер обучения машины в облаке](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-in-the-cloud)

### <a name="configuring-machine-learning-server-or-r-server-to-support-web-services"></a>Настройка машины обучения сервера или R Server для поддержки веб-служб

При использовании виртуальной машины, которая включает сервер обучения машины Дополнительные настройки может потребоваться использовать развертывание веб-служб, удаленное выполнение, или использовать виртуальную машину в качестве сервера развертывания в вашей организации.

Инструкции см. в разделе [Настройка машины обучения сервера для эксплуатации analytics](https://docs.microsoft.com/machine-learning-server/operationalize/configure-machine-learning-server-one-box).

Если требуется использовать пакеты, такие как RevoScaleR или MicrosoftML не требуется дополнительная настройка.

## <a name="bkmk_list"></a>Список виртуальных машин

В настоящее время для машинного обучения с помощью SQL Server доступны следующие виртуальные машины.

|Название| Комментарии|
|----|----|----|
| **SQL Server 2016**| ***  |
|SQL Server 2016 Enterprise с пакетом обновления 1 для Windows|Службы R для интеграции расширенной аналитики.|
|BYOL SQL Server 2016 SP1 Enterprise на Windows Server |Службы R для интеграции расширенной аналитики. |
|Бесплатная лицензия: SQL Server 2016 Developer с пакетом обновления 1 на Windows Server 2016 |Службы R для интеграции расширенной аналитики. |
| Виртуальная машина анализа данных — Windows 2012|Содержит популярных средств для обработки и анализа данных, включая Microsoft R Server Developer Edition, SQL Server 2016 Developer edition, распространения Anaconda Python, Юлия профессионального выпуска developer и записные книжки Jupyter для R.| 
| Виртуальная машина анализа данных — Windows 2016|Включает SQL Server 2016 Developer Edition с поддержкой аналитика R в базе данных.|
|**SQL Server 2017**| ***   |
|SQL Server 2017 г предприятия Windows Server 2016| Службы обучения компьютера с поддержкой языка Python и R.|
|BYOL SQL Server 2017 г предприятия Windows Server 2016|Службы обучения компьютера с поддержкой языка Python и R.|
| Лицензия свободного SQL Server: SQL Server 2017 г Developer на Windows Server|Службы обучения компьютера с поддержкой языка Python и R.|
| **Другое**| *** |
| Машинного обучения сервера только SQL Server 2017 г Enterprise|Аналогично образа SQL Server 2016 Enterprise, но содержит автономной версии сервера Machine обучения и имеет ядро ScaleR, и функциональные возможности ввода в эксплуатацию оптимизирован для Windows сред.|
| Сервер машинного обучения для Windows|Содержит автономной версии сервера Machine обучения, с функциями ввода в эксплуатацию, оптимизированный для среды Windows.|
|Виртуальная машина анализа данных |Выпуски Linux, включающие R Server. Виртуальные машины Linux, которые включают 2017 г. SQL Server не могут выполнять код R или Python в SQL Server. Тем не менее можно выполнить оценки на обученной модели с помощью функции ПРОГНОЗИРОВАНИЯ T-SQL. Дополнительные сведения см. в разделе [собственного оценки в SQl Server](../sql-native-scoring.md).|
