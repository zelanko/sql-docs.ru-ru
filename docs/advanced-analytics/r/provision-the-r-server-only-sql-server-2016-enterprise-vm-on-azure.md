---
title: "Подготовка виртуальной машины SQL Server 2016 Enterprise только с R Server в Azure"
ms.custom: 
ms.date: 06/05/2017
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
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a3bfca0753984f09220d8ca4e4f6933c949daf2b
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="advanced-analytics-virtual-machines-on-azure"></a>Дополнительные аналитические функции виртуальных машин в Azure

Виртуальные машины в Azure — это возможность быстро настроить полный серверной среде для машинного обучения решения. В этом разделе перечислены некоторые образы виртуальных машин, которые содержат R Server, SQL Server с помощью машинного обучения или другие средства обработки и анализа данных из Microsoft.

> [!TIP]
> Мы рекомендуем использовать новую версию портала Azure и Azure Marketplace. Некоторые рисунки недоступны при просмотре коллекции на классическом портале Azure.

В Azure Marketplace содержит несколько виртуальных машин, которые поддерживают обработки и анализа данных. Этот список не является полноту, но предоставляет только имена изображений, использующих Microsoft R Server или SQL Server машинного самообучения, службы, чтобы облегчить поиск.

## <a name="how-to-provision-a-vm"></a>Подготовка виртуальной Машины

Если вы не знакомы с помощью виртуальных машинах Azure, мы рекомендуем, отображается в следующих статьях, Дополнительные сведения об использовании портала и настройка виртуальной машины.

+ [Виртуальные машины — приступая к работе](https://azure.microsoft.com/documentation/learning-paths/virtual-machines/)
+ [Приступая к работе с виртуальными машинами Windows](https://azure.microsoft.com/en-us/documentation/articles/virtual-machines-windows-hero-tutorial/)

### <a name="find-an-image"></a>Найти изображение

1. Панели мониторинга Azure, щелкните **Marketplace**.

    - Нажмите кнопку **-аналитику** или **баз данных**, а затем введите «R» в **фильтра** управления, чтобы просмотреть список виртуальных машин R Server.
    - Другие возможные строки для **фильтра** управления *обработки и анализа данных* и *машинное обучение*
    - Использовать подстановочный знак % поиска для поиска имен виртуальных Машин, которые содержат целевой строки, таких как *R* или *Юлия*.

2. Чтобы получить R Server для Windows, выберите **R Server только SQL Server 2016 Enterprise**.
  
    [R Server](https://msdn.microsoft.com/microsoft-r/rserver-whats-new) лицензируется как компонент SQL Server Enterprise Edition, но версии 9.1. установлен как автономный сервер и обслуживание под политику поддержки современных жизненного цикла.

3. После создания и запуска виртуальной машины нажмите кнопку **Подключение** , чтобы установить подключение и войти на новую машину.

4. После подключения, может потребоваться установить дополнительные средства R или средства разработки.

### <a name="install-additional-r-tools"></a>Установка дополнительных средств R

По умолчанию Microsoft R Server включает все средства R, устанавливаемые при базовой установке R, включая RTerm и RGui. На случай, если вы захотите сразу же приступить к использованию R, на рабочий стол был добавлен ярлык RGui.

Тем не менее может потребоваться установить дополнительные средства R, например RStudio, средства R для Visual Studio (RTVS) или Microsoft R клиента. Ниже приведены ссылки на расположения скачивания и инструкции:
+ [Средства R для Visual Studio](https://docs.microsoft.com/visualstudio/rtvs/installation)
+ [Microsoft R Client](https://msdn.microsoft.com/microsoft-r/install-r-client-windows)
+ [RStudio для Windows](https://www.rstudio.com/products/rstudio/download/)

После завершения установки измените расположения по умолчанию среды выполнения R, чтобы все средства разработки R использовали библиотеки R Server.

### <a name="configure-server-for-web-services"></a>Настройка сервера для веб-служб

Если виртуальная машина содержит R Server, для использования развертывания веб-служб, удаленного выполнения или использования R Server как сервера развертывания в организации понадобятся дополнительные настройки. Инструкции см. в статье [Configure R Server for Operationalization](https://msdn.microsoft.com/microsoft-r/operationalize/configuration-initial) (Настройка R Server для ввода в эксплуатацию).

> [!NOTE]
> Если требуется использовать пакеты, такие как RevoScaleR или MicrosoftML не требуется дополнительная настройка.

## <a name="r-server-images"></a>R Server изображений

### <a name="microsoft-data-science-virtual-machine"></a>Виртуальная машина анализа данных Microsoft

Настроена с Microsoft R Server, а также Python (дистрибутив Anaconda), Блокнота jupyter, выпуск Visual Studio Community, Power BI Desktop, пакет SDK Azure и SQL Server Express edition.

Версия Windows выполняется в Windows Server 2012, а также содержит специальные инструменты для моделирования и анализа, включая CNTK и mxnet, популярные пакеты R, например xgboost и Vowpal Wabbit.

### <a name="linux-data-science-virtual-machine"></a>Виртуальная машина анализа данных Linux

Также содержит популярных средств для данных научных вычислений и разработки действий, включая Microsoft R Open, Microsoft R Server Developer Edition, Anaconda Python и Jupyter ноутбуков Python, R и Юлия.

Этот образ виртуальной Машины были недавно добавлены JupyterHub открытой программное обеспечение, которое позволяет использовать несколько пользователей через разными методами проверки подлинности, включая локальной проверки подлинности учетной записи ОС и проверка подлинности учетной записи Github. JupyterHub является вариантом особенно полезна, если вы хотите запустить учебный курс и хотите всех студентов, совместно использовать тот же сервер, но использовать отдельный записных книжек и каталоги.

Образы предназначены для Ubuntu Centos и Centos CSP.

### <a name="r-server-only-sql-server-2016-enterprise"></a>R Server только SQL Server 2016 Enterprise

Эта виртуальная машина содержит автономный установщик для [R Server 9.1.](https://msdn.microsoft.com/microsoft-r/rserver-whats-new) который поддерживает новую модель лицензирования современных жизненного цикла программного обеспечения.

 R Server доступен также в образы для версии Linux CentOS 7.2, версии Linux RedHat 7.2 и Ubuntu версии 16.04.

 > [!NOTE]
 > Эти виртуальные машины заменяют **виртуальную машину RRE для Windows**, которая была доступна в Azure Marketplace ранее.

## <a name="sql-server-images"></a>Образы SQL Server

Для использования служб R (в базе данных) или службах обучения машин, необходимо установить одну из виртуальных машин SQL Server Enterprise или Developer edition и добавить службе машинного обучения, как описано здесь: [Установка SQL Server R Services Виртуальная машина Azure](../../advanced-analytics/r-services/installing-sql-server-r-services-on-an-azure-virtual-machine.md).

> [!NOTE]
> В настоящее время службы обучения машины не поддерживается на виртуальных машинах Linux 2017 г. SQL Server или в базе данных SQL Azure. Необходимо использовать SQL Server 2016 SP1 или 2017 г. SQL Server для Windows.

Виртуальная машина анализа данных также включает SQL Server 2016 с компонентом служб R, который уже включен.


## <a name="other-vms"></a>Другие виртуальные машины

### <a name="deep-learning-toolkit-for-the-data-science-virtual-machine"></a>Глубокое изучение набора средств для виртуальная машина анализа данных

Эта виртуальная машина содержит же машинного обучения средств, доступных для обработки и анализа данных в виртуальной машине, но с версиями GPU mxnet, CNTK, TensorFlow и Keras. Этот образ можно использовать только на экземплярах Azure GPU N-й серии. 

Набор средств углубленного обучения также предоставляет набор образцов глубокого изучения решений, использующих GPU, включая распознавание изображений в базе данных CIFAR 10 и образец распознавания символов в базе данных MNIST. Экземпляры GPU в настоящее время доступны в центральных штатах юга США, восток США, Западная Европа и Юго-Восточная Азия.

> [!IMPORTANT]
> Сейчас экземпляры графических процессоров доступны только в юго-центральном регионе США.


## <a name="frequently-asked-questions"></a>Часто задаваемые вопросы

### <a name="can-i-install-a-virtual-machine-with-sql-server-2017"></a>Можно установить виртуальную машину с SQL Server 2017 г.

Изображения теперь отображаются доступные, содержащие 2017 г CTP-версия SQL Server 2.0 для сред Linux, но эти среды в настоящее время не поддерживают службы обучения машины. 

Виртуальную машину под управлением Windows для SQL Server 2017 г Enterprise Edition, включающий службы обучения машины будут доступны после общедоступный выпуск. 

В качестве альтернативы можно использовать образ SQL Server 2016 и обновите экземпляр r, как описано здесь: [обновление экземпляра с помощью SqlBindR](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md). 

Создание виртуальной машины или загрузить предварительную версию CTP 2.0 [2017 г. SQL Server](https://www.microsoft.com/sql-server/sql-server-2017).

### <a name="how-do-i-access-data-in-an-azure-storage-account"></a>Как получить доступ к данным в учетной записи хранения Azure?

Если вам нужно использовать данные из своей учетной записи хранения Azure, существует несколько вариантов доступа к данным или их перемещения:

+ Скопируйте данные из вашей учетной записи хранения в локальную файловую систему с помощью служебной программы, например [AzCopy](https://azure.microsoft.com/documentation/articles/storage-use-azcopy/#copy-files-in-azure-file-storage-with-azcopy-preview-version-only). 

+ Добавьте файлы в общую папку в вашей учетной записи хранения и затем подключите ее как сетевой диск в виртуальной машине.  Дополнительные сведения см. в разделе [Mounting Azure files](https://azure.microsoft.com/documentation/articles/storage-dotnet-how-to-use-files/)(Подключение файлов Azure). 

### <a name="how-do-i-use-data-from-azure-data-lake-storage-adls"></a>Как использовать данные из хранилища Azure Data Lake (ADLS)?

Может считывать данные из хранилища ADLS, с помощью RevoScaleR, при ссылке таким же образом HDFS файловой системы, с помощью webHDFS учетной записи хранилища.  Дополнительные сведения см. в разделе этой статьи: [с помощью R для выполнения операций файловой системы в хранилище Озера данных Azure](https://blogs.msdn.microsoft.com/microsoftrservertigerteam/2017/03/14/using-r-to-perform-filesystem-operations-on-azure-data-lake-store/).

## <a name="see-also"></a>См. также:

[Службы R SQL Server](https://msdn.microsoft.com/library/mt604845.aspx)


