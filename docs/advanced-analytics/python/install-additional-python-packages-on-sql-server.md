---
title: "Установить новые пакеты Python на сервере SQL Server | Документы Microsoft"
ms.date: 01/04/2018
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: python
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 21456462-e58a-44c3-9d3a-68b4263575d7
caps.latest.revision: 
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: On Demand
ms.openlocfilehash: 68c3c0c3699455854ac23fed7befb042eaf17155
ms.sourcegitcommit: 99102cdc867a7bdc0ff45e8b9ee72d0daade1fd3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/11/2018
---
# <a name="install-new-python-packages-on-sql-server"></a>Установить новые пакеты Python на сервере SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этой статье описывается установка новые пакеты Python в экземпляре 2017 г. SQL Server.

Также описывается перечисление пакетов, установленных в текущей среде.

## <a name="prerequisites"></a>предварительные требования

Установка новых пакетов во многом похожи в стандартной среде Python. Однако некоторые дополнительные действия требуются, если сервер не подключен к Интернету.

+ Необходимо установить службы обучения машины (в базе данных) с параметром языка Python. Инструкции см. в разделе [Настройка службы обучения Python машины](setup-python-machine-learning-services.md).

+ Для каждого экземпляра сервера необходимо установить отдельную копию пакета. Пакеты не могут использоваться совместно экземпляров.

+ Определяют, будет ли работать пакета, который будет использоваться с версии 3.5 Python и в среде Windows. 

    Как правило существует несколько ограничений в пакетах, которые можно импортировать и использовать в среде SQL Server. Возможны следующие проблемы, использующие функции сетевого взаимодействия, будет заблокирован на сервере или брандмауэром, или пакеты с зависимостями, которые нельзя установить на компьютере Windows.

+ Для установки пакетов требуется административный доступ к серверу.

## <a name="add-a-new-python-package"></a>Добавить новый пакет Python

Например предположим, требуется установить новый пакет непосредственно на сервере SQL Server.

Пакет установки в этом примере [CNTK](https://docs.microsoft.com/cognitive-toolkit/), платформа для углубленного обучения корпорации Майкрософт, который поддерживает настройку, обучения и совместное использование различных типов нейронных сетей.

> [!TIP]
> Нужна помощь с настройкой средства Python? См. в следующих блогах:
> 
> [Начало работы с Python веб-служб с помощью сервера машины обучения](https://blogs.msdn.microsoft.com/mlserver/2017/12/13/getting-started-with-python-web-services-using-machine-learning-server/)
> 
> [Мошенник Дэвид: Набор средств Майкрософт для Когнитивных + VS Code](http://dacrook.com/cntk-vs-code-awesome/)

### <a name="step-1-download-the-windows-version-of-the-python-package"></a>Шаг 1. Загрузите версию Windows пакета Python

+ При установке пакетов Python на сервере без доступа к Интернету, необходимо загрузить его WHL на другом компьютере и скопируйте его на сервер.

    Например, на отдельном компьютере, можно загрузить файл WHL с этого сайта [https://cntk.ai/PythonWheel/CPU-Only](https://cntk.ai/PythonWheel/CPU-Only/cntk-2.1-cp35-cp35m-win_amd64.whl), а затем скопируйте файл `cntk-2.1-cp35-cp35m-win_amd64.whl` в локальную папку на компьютере SQL Server.

+ 2017 г. SQL Server использует Python 3.5. Убедитесь, что версия пакета для Windows и версии, совместимой с Python 3.5.

Эта страница содержит загружаемые файлы для нескольких платформ, а также для нескольких версий Python: [Настройка CNTK](https://docs.microsoft.com/cognitive-toolkit/Setup-CNTK-on-your-machine)

### <a name="step-2-open-a-python-command-prompt"></a>Шаг 2. Откройте командную строку Python

Найдите расположение библиотеки Python по умолчанию, используемый сервером SQL Server. Если установлено несколько экземпляров, убедитесь, что перейдите в папку PYTHON_SERVICE для экземпляра, в которой вы хотите добавить пакет.

Например если установлены службы обучения машины, используя значения по умолчанию и машинное обучение включен на экземпляре по умолчанию, путь будет следующим:

    `C:\Program Files\Microsoft SQL  Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES`

Откройте командную строку Python, связанный с экземпляром.

> [!TIP]
> Рекомендуется настроить среду Python конкретной машины обучения Server или SQL Server.

### <a name="step-3-install-the-package-using-pip"></a>Шаг 3. Установите пакет, с помощью pip

+ Если вы привыкли Python командной строки, используйте PIP.exe для установки новых пакетов. Можно найти **pip** установщика `Scripts` вложенную папку. 

    Если вы получаете сообщение об **pip** не распознается как внутренняя или внешняя команда, можно добавить путь к исполняемому файлу Python и папке сценариев Python в переменную PATH в Windows.

    Полный путь к **сценариев** в установке по умолчанию таков:

    `C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\Scripts`

+ Если вы используете 2017 г. Visual Studio или Visual Studio 2015 с расширениями Python, можно запустить `pip install` из **среды Python** окна. Нажмите кнопку **пакетов**и в текстовом поле введите имя или расположение для установки пакета. Вам не нужно ввести `pip install`; он заполняется для вас автоматически. 

    - Если компьютер имеет доступ к Интернету, укажите имя пакета или URL-адрес пакета и версия. Например чтобы установить версию CNTK, которая поддерживается для Windows и Python 3.5, можно указать URL-адрес загрузки:`https://cntk.ai/PythonWheel/CPU-Only/cntk-2.1-cp35-cp35m-win_amd64.whl`

    - Если компьютер не имеет доступа к Интернету, вы должны WHL-файл был загружен заранее. Укажите локальный путь к файлу и имя. Например вставьте следующий путь и файл для установки файла WHL, загрузив его с сайта:`"C:\Downloads\CNTK\cntk-2.1-cp35-cp35m-win_amd64.whl"`

Может потребоваться повысить права для завершения установки.

В процессе установки можно видеть состояние сообщения в окне командной строки:

```python
pip install https://cntk.ai/PythonWheel/CPU-Only/cntk-2.1-cp35-cp35m-win_amd64.whl
Collecting cntk==2.1 from https://cntk.ai/PythonWheel/CPU-Only/cntk-2.1-cp35-cp35m-win_amd64.whl
  Downloading https://cntk.ai/PythonWheel/CPU-Only/cntk-2.1-cp35-cp35m-win_amd64.whl (34.1MB)
    100% |################################| 34.1MB 13kB/s
...
Installing collected packages: cntk
Successfully installed cntk-2.1
```



### <a name="step-4-load-the-package-or-its-functions-as-part-of-your-script"></a>Шаг 4. Загрузить пакет или его функции как часть сценария

По завершении установки можно немедленно начать с использованием пакета, как описано в следующем шаге.

Примеры для углубленного обучения с помощью CNTK, см. в этих учебниках: [API Python для CNTK](https://cntk.ai/pythondocs/tutorials.html)

Чтобы использовать функции из пакета в скрипте, вставьте стандартный `import <package_name>` инструкции в начальной строки скрипта:

```python
import numpy as np
import cntk as cntk
cntk._version_
```

##  <a name="how-to-view-installed-packages-using-conda"></a>Просмотр установленных пакетов с помощью conda

Можно различными способами, которые можно получить список установленных пакетов. Например, можно просмотреть установленные пакеты в **среды Python** windows из Visual Studio.

При использовании в командной строке Python, можно использовать **conda** диспетчер пакетов, которые входят в среду Anaconda Python, добавить программа установки SQL Server.

Чтобы просмотреть пакеты Python, которые были установлены в текущей среде, выполните следующую команду из командной строки windows:

```python
conda list
```

Дополнительные сведения о **conda** и как использовать его для создания и управления несколькими среды Python см. в разделе [управление средами с conda](https://conda.io/docs/user-guide/tasks/manage-environments.html).
