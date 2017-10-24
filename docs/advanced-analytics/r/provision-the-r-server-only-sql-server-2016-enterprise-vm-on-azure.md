---
title: "Подготовьте виртуальную машину для машинного обучения в Azure | Документы Microsoft"
ms.custom: 
ms.date: 10/16/2017
ms.prod: r-server
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c8826df7-aa67-4768-baa9-bdc875c4a766
caps.latest.revision: 12
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 8cc1fcfdeae8742a93916dfb08c9db1215f88721
ms.openlocfilehash: 7cb9e069fc3b537f8aab9d048a152435ad0cc6ac
ms.contentlocale: ru-ru
ms.lasthandoff: 10/17/2017

---
# <a name="provision-a-virtual-machine-for-machine-learning-on-azure"></a>Подготовьте виртуальную машину для машинного обучения в Azure

Виртуальные машины в Azure — это возможность быстро настроить полный серверной среде для машинного обучения решения. В этой статье перечислены некоторые образы виртуальных машин, которые содержат R Server, машины обучения Server или SQL Server с помощью машинного обучения.

Этот список не является полноту, но предоставляет только имена изображений, которые связаны с машины обучения Server или SQL Server машины обучения, чтобы облегчить поиск.

> [!TIP]
> Мы рекомендуем использовать новую версию портала Azure и Azure Marketplace. Некоторые рисунки недоступны при просмотре коллекции на классическом портале Azure.

## <a name="how-to-provision-a-virtual-machine"></a>Подготовка виртуальной машины

Если вы не знакомы с помощью виртуальных машинах Azure, мы рекомендуем, отображается в следующих статьях, Дополнительные сведения об использовании портала и настройка виртуальной машины.

+ [Виртуальные машины — приступая к работе](https://azure.microsoft.com/documentation/learning-paths/virtual-machines/)
+ [Приступая к работе с виртуальными машинами Windows](https://azure.microsoft.com/documentation/articles/virtual-machines-windows-hero-tutorial/)

## <a name="find-a-machine-learning-image"></a>Найти образ машины обучения

1. На портале Azure (portal.azure.com), нажмите кнопку **виртуальные машины**, или нажмите кнопку **New**.

2. Найдите поле поиска в верхней части страницы, который можно использовать для фильтрации результатов по имени. 

3. Введите «R Server» (или «ML Server») в **фильтра** управления, чтобы просмотреть список связанных ресурсов. Нажмите кнопку **поиска в Marketplace** для просмотра виртуальных машин.

    > [!TIP]
    > 
    > Другие возможные строки для элемента управления фильтра являются «обработки и анализа данных» и «машинное обучение».
    > 
    > Используйте `%` подстановочный знак в поиск, чтобы найти имена виртуальных машин. Например, можно ввести `"`% % Юлия` or `%R % ".

4. Чтобы получить R Server для Windows, выберите **R Server только SQL Server 2016 Enterprise**.
  
    [R Server](https://msdn.microsoft.com/microsoft-r/rserver-whats-new) лицензируется как компонент SQL Server Enterprise Edition, но версии 9.1 установлен как автономный сервер и обрабатывается в соответствии с политикой поддержки современных жизненного цикла.

    > [!NOTE] 
    > 
    > Это входит в диапазон, просмотрите для выпуска новой виртуальной машины, который включает 2017 г. SQL Server и 9.2.1 выпуска машины Server обучения.
    > До этого времени может обновить версию SQL Server установлен на этой виртуальной машине, используя Центр установки SQL Server и выборе режима обновления. Дополнительные сведения см. в разделе [обновление SQL Server с помощью мастера установки](https://docs.microsoft.com/sql/database-engine/install-windows/upgrade-sql-server-using-the-installation-wizard-setup).

5. Виртуальная машина будет создана и запущена, нажмите кнопку **Connect** кнопку, чтобы открыть соединение и войдите в систему на новом компьютере.

5. После подключения можно установить дополнительный пакет R или средстве разработки предпочтительным.

### <a name="install-additional-r-tools"></a>Установка дополнительных средств R

По умолчанию Microsoft R Server включает все средства R, устанавливаемые при базовой установке R, включая RTerm и RGui. Ярлык для RGui также были добавлены к рабочему столу.

Тем не менее может потребоваться установить дополнительные средства R, например RStudio, средства R для Visual Studio (RTVS) или Microsoft R клиента. Ниже приведены ссылки на расположения скачивания и инструкции:

+ [Средства R для Visual Studio](https://docs.microsoft.com/visualstudio/rtvs/installation)
+ [Microsoft R Client](https://msdn.microsoft.com/microsoft-r/install-r-client-windows)
+ [RStudio для Windows](https://www.rstudio.com/products/rstudio/download/)

После завершения установки измените расположения по умолчанию среды выполнения R, чтобы все средства разработки R использовали библиотеки R Server.

### <a name="configure-r-server-to-support-web-services"></a>Настроить сервер R для поддержки веб-служб

Использование развертывания веб-службы, удаленного выполнения или для возможности использования R Server в качестве сервера развертывания в вашей организации требуется дополнительная настройка. Инструкции см. в разделе [Настройка R Server для ввода в эксплуатацию analytics](https://docs.microsoft.com/machine-learning-server/install/operationalize-r-server-one-box-config).

> [!NOTE]
> Если требуется использовать пакеты, такие как RevoScaleR или MicrosoftML не требуется дополнительная настройка.

## <a name="other-virtual-machines"></a>Другие виртуальные машины

Следующие изображения доступны из Azure Marketplace и включают полностью настроенный машинного обучения средства, но не обязательно должны включать SQL Server.

### <a name="data-science-virtual-machine"></a>Виртуальная машина анализа данных

Этот образ предварительно настроен с Microsoft R Server, а также Python (дистрибутив Anaconda), Блокнота jupyter, выпуск Visual Studio Community, Power BI Desktop, пакет SDK Azure и SQL Server Express edition.

Версия Windows выполняется в Windows Server 2012, а также содержит специальные инструменты для моделирования и анализа, включая [CNTK](https://www.microsoft.com/cognitive-toolkit/), [mxNet](https://mxnet.incubator.apache.org/), и популярные R пакеты, такие как **xgboost**.

Выпуски Linux предоставляются для Ubuntu Centos и Centos CSP и содержать много популярных средств для операций обработки и анализа и разработки данных.

Дополнительные сведения см. в разделе [введение в Azure виртуальная машина анализа данных для Linux и Windows](https://docs.microsoft.com/azure/machine-learning/data-science-virtual-machine/provision-vm).

Этот образ недавно был обновлен для включения: 

+ Поддержка Юлия языка обработки и анализа данных масштабируемых, мощные будущего 
+ JupyterHub является полезным для запуска учебный курс и хотите всех студентов, совместно использовать тот же сервер, но использовать отдельный записных книжек и каталоги.

Дополнительные сведения о поддерживаемых средствах и обучения платформы компьютера в разделе [познакомиться виртуальная машина анализа данных](https://docs.microsoft.com/azure/machine-learning/data-science-virtual-machine/dsvm-tools-overview)

### <a name="r-server-virtual-machines"></a>R Server виртуальные машины

В дополнение к **R Server только SQL Server 2016 Enterprise** изображения, можно получить автономных виртуальных машин, которые содержат R Server. Для версии Linux CentOS 7.2, версии Linux RedHat 7.2 и Ubuntu версии 16.04 доступны изображения.

Дополнительные сведения см. в разделе [сервер обучения машины в облаке](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-in-the-cloud)

 > [!NOTE]
 > Эти виртуальные машины заменяют **виртуальную машину RRE для Windows**, которая была доступна в Azure Marketplace ранее.

### <a name="sql-server-virtual-machines"></a>Виртуальные машины SQL Server

Существует два варианта использования машинного самообучения в Azure, SQL Server:

+ Получение одного из образов виртуальной машины, которая включает предварительно установить SQL Server R Services.
+ Создание виртуальной машины Azure и установка SQL Server Enterprise или Developer edition, с помощью лицензионный ключ. 
  
    Запустите программу установки еще раз, чтобы добавить и включить службу машинного обучения, как описано здесь: [Установка служб SQL Server R на виртуальной машине Azure](../r/installing-sql-server-r-services-on-an-azure-virtual-machine.md).
+ Создание базы данных SQL Azure с помощью уровня службы, которые поддерживают машинного обучения и в настоящее время используют новый компонент служб R в режиме предварительного просмотра. Дополнительные сведения см. в разделе [базу данных SQL Azure](../r/using-r-in-azure-sql-database.md).

> [!NOTE]
> В настоящее время службы обучения машины SQL Server не поддерживается на виртуальных машинах Linux для 2017 г. SQL Server. Тем не менее можно выполнить оценки на обученной модели с помощью функции ПРОГНОЗИРОВАНИЯ T-SQL. Дополнительные сведения см. в разделе [собственного оценки в SQl Server](../sql-native-scoring.md). 

### <a name="virtual-machines-for-deep-learning"></a>Виртуальные машины для углубленного обучения 

Ранее Корпорация Майкрософт предоставляет глубокой Toolkit обучения для виртуальная машина анализа данных, который можно добавить в существующий виртуальная машина анализа данных. Этот набор средств теперь заменяется глубокой обучения виртуальной машине, который содержит средства популярных углубленного обучения:

+ Выпуски GPU углубленного обучения платформ, таких как Когнитивных набор средств Майкрософт, TensorFlow, Keras и Caffe
+ Встроенные драйверы GPU
+ Набор средств для обработки текста и изображений
+ Enterprise инструментами разработки, например Microsoft R Server Developer Edition Anaconda Python, записные книжки Jupyter Python и R
+ Средства разработки для Python, R, SQL Server и многое другое
+ Образцы конца в конец понимание текст и изображения

Глубокие обучения виртуальной машины доступен на Windows 2016 или платформы Ubuntu Linux. Дополнительные сведения см. в разделе [углубленного обучения и AI платформы](https://docs.microsoft.com/azure/machine-learning/data-science-virtual-machine/dsvm-deep-learning-ai-frameworks).

> [!IMPORTANT]
> 
> Для развертывания этой виртуальной машины требуется образы виртуальных машин серии Azure GPU NC, доступные в ограниченной регионах Azure. Сведения о доступности см. в разделе [продукты, доступные по регионам](https://azure.microsoft.com/en-us/regions/services/). При подготовке виртуальной машины, обязательно используйте **HDD** как тип диска не **SSD**.

## <a name="frequently-asked-questions"></a>Часто задаваемые вопросы

Этот раздел содержит некоторые распространенные вопросы о машинного обучения виртуальных машин от корпорации Майкрософт.

### <a name="can-i-install-a-virtual-machine-with-sql-server-2017"></a>Можно установить виртуальную машину с SQL Server 2017 г.

Виртуальную машину под управлением Windows для SQL Server 2017 г Enterprise Edition, включающий службы обучения машины скоро будет доступна. Найдите объявления на этих узлах блоги:

+ [Cortana аналитики и машинное обучение](https://blogs.technet.microsoft.com/machinelearning/)
+ [Инсайдера разработки платформы данных](https://blogs.technet.microsoft.com/dataplatforminsider/)

### <a name="how-do-i-access-data-in-an-azure-storage-account"></a>Как получить доступ к данным в учетной записи хранения Azure?

Если вам нужно использовать данные из своей учетной записи хранения Azure, существует несколько вариантов доступа к данным или их перемещения:

+ Скопируйте данные из вашей учетной записи хранения в локальную файловую систему с помощью служебной программы, например [AzCopy](https://azure.microsoft.com/documentation/articles/storage-use-azcopy/#copy-files-in-azure-file-storage-with-azcopy-preview-version-only). 

+ Добавьте файлы в общую папку в вашей учетной записи хранения и затем подключите ее как сетевой диск в виртуальной машине.  Дополнительные сведения см. в разделе [Mounting Azure files](https://azure.microsoft.com/documentation/articles/storage-dotnet-how-to-use-files/)(Подключение файлов Azure). 

### <a name="how-do-i-use-data-from-azure-data-lake-storage-adls"></a>Как использовать данные из хранилища Azure Data Lake (ADLS)?

Может считывать данные из хранилища ADLS, с помощью RevoScaleR, при ссылке таким же образом HDFS файловой системы, с помощью webHDFS учетной записи хранилища.  Дополнительные сведения см. в разделе этой статьи: [с помощью R для выполнения операций файловой системы в хранилище Озера данных Azure](https://blogs.msdn.microsoft.com/microsoftrservertigerteam/2017/03/14/using-r-to-perform-filesystem-operations-on-azure-data-lake-store/).



