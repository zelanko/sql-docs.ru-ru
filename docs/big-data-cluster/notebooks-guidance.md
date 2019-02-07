---
title: Запуск записных книжек в Azure Data Studio
titleSuffix: SQL Server 2019 big data clusters
description: В этой статье объясняется, как запустить записные книжки Jupyter в Azure Data Studio conneected в кластер SQL Server 2019 больших данных.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 12/12/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: e4f1c945bd09c4d2878ebb441027e32898f24c56
ms.sourcegitcommit: f8ad5af0f05b6b175cd6d592e869b28edd3c8e2c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/07/2019
ms.locfileid: "55807474"
---
# <a name="how-to-use-notebooks-in-sql-server-2019-preview"></a>Как использовать записные книжки в предварительной версии SQL Server 2019

В этой статье описывается, как запускать записные книжки Jupyter в кластере большие данные и как начать создание собственных записных книжек. Также показано, как отправлять задания, к кластеру.

## <a name="prerequisites"></a>предварительные требования

Использовать записные книжки, необходимо установить следующие компоненты:

- [Кластер SQL Server 2019 больших данных](deployment-guidance.md)
- [Средства SQL Server 2019 больших данных](deploy-big-data-tools.md):
   - **Azure Data Studio**
   - **Расширение SQL Server 2019**
   - **kubectl**

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a name="connect-to-the-sql-server-big-data-cluster-end-point"></a>Подключение к конечной точке кластера больших данных сервера SQL

Вы можете подключиться к разные конечные точки в кластере. Можно подключиться к типу соединения Microsoft SQL Server или в конечную точку кластера больших данных SQL Server.
В студии данных Azure (Предварительная версия), нажмите клавишу F1 и нажмите кнопку **новое подключение** и вы можете подключиться к вашей конечной точки кластера больших данных SQL Server.

![изображение 1](media/notebooks-guidance/image1.png)

## <a name="browse-hdfs"></a>Обзор HDFS

После подключения вы сможете просмотреть папку HDFS. SQL Server запускается WebHDFS запускается после завершения развертывания. С помощью WebHDFS, вы можете **обновить**, добавьте **новый каталог**, **отправить** файлы, и **удалить**.

![изображение2](media/notebooks-guidance/image2.png)

Эти простые операции позволяют предоставить свои данные в HDFS.

## <a name="launch-new-notebooks"></a>Запустить новые записные книжки

>[!NOTE]
>Если у вас есть несколько Python процессы, запущенные в вашей среде, сначала удалите `.scaleoutdata` папку в каталоге установленных. Это инициирует `Reinstall Notebook dependencies` задачи студии данных Azure. Может занять несколько минут для всех зависимостей должны быть установлены.

При возникновении проблем с установкой зависимости записную книжку, нажмите кнопку Ctrl + Shift + P или для Macintosh Cmd + Shift + P и типа `Reinstall Notebook dependencies` в палитре команд.

![image3](media/notebooks-guidance/image3.png)

Существует несколько способов, чтобы запустить записную книжку.

1. Из **управление информационной панели**. После установления нового подключения, вы увидите панель мониторинга. Нажмите кнопку **новой записной книжки** задачи с помощью панели мониторинга.
  
    ![image4](media/notebooks-guidance/image4.png)

1. Щелкните правой кнопкой мыши подключение HDFS/Spark и нажмите кнопку **новой записной книжки** в контекстном меню.

    ![image5](media/notebooks-guidance/image5.png)

    Новый файл с именем `Notebook-0.ipynb` открывается.

    ![image6](media/notebooks-guidance/image6.png)

При открытии записной книжки из палитру команд, записная книжка откроется как `Untitled-0.ipynb`.

## <a name="supported-kernels-and-attach-to-context"></a>Поддерживаемые версии ядра и присоединить к контексту

Установка записной книжки поддерживает ядрами PySpark и Spark, волшебной команды Spark, которые позволяют писать код Python и Scala, с помощью Spark. При необходимости можно выбрать Python целях локальной разработки.

![image7](media/notebooks-guidance/image7.png)

При выборе одного из этих ядер, установки настраивает этого ядра в виртуальной среде и написания кода на поддерживаемых языках.

|Ядра|Описание
|:-----|:-----
|PySpark3 и ядро PySpark| Пишите код Python, используя Spark вычислений из кластера.
|Ядро Spark|Напишите код для Scala и R с помощью Spark вычислений из кластера.
|Ядро Python|Напишите код Python для локальной разработки.

`Attach to` предоставляет контекст для ядра для присоединения. При подключении к SQL Server больших данных кластера конечную точку по умолчанию `Attach to` является конечной точки кластера.

Когда вы не подключены к конечной точке кластера больших данных SQL Server, ядра по умолчанию используется Python и `Attach to` является `localhost`.

## <a name="hello-world-in-different-contexts"></a>Hello world в различных контекстах

### <a name="pyspark3pyspark-kernel"></a>Ядро Pyspark3/PySpark

Выберите ядро PySpark и в тип ячейки в следующем коде.

Нажмите кнопку **Запустить**.

Приложения Spark запускается и возвращает следующие выходные данные:

![image8](media/notebooks-guidance/image8.png)

### <a name="spark-kernel--scala-language"></a>Ядро Spark | Язык Scala

Выберите Spark | Scala ядра и тип ячейки в следующем коде.

![image9](media/notebooks-guidance/image9.png)

Добавьте новую ячейку кода, нажав кнопку **+ Code** команды на панели инструментов.

Теперь выберите Spark | Scala в раскрывающемся списке для ядра, а в ячейке введите или вставьте в —

![Image10](media/notebooks-guidance/image10.png)

Вы также можете просмотреть «Параметры ячейки», при нажатии на значок "Параметры" ниже.

![Image11](media/notebooks-guidance/image11.png)

### <a name="spark-kernel--r-language"></a>Ядро Spark | Язык R

Выберите Spark | R в раскрывающемся списке для ядра. В ячейке введите или вставьте в него код. Нажмите кнопку **запуска** чтобы увидеть следующие выходные данные.

![Image13](media/notebooks-guidance/image13.png)

### <a name="local-python-kernel"></a>Локальное ядро Python

Выберите локальное ядро Python и в тип ячейки в -

![Image14](media/notebooks-guidance/image14.png)

### <a name="markdown-text"></a>Текст с разметкой markdown

Добавьте новую ячейку текст, нажав кнопку **+ текст** команды на панели инструментов.

![Image15](media/notebooks-guidance/image15.png)

Дважды щелкните внутри ячейки текста для изменения, чтобы изменить представление 

![Image16](media/notebooks-guidance/image16.png)

Изменения ячейки в режим редактирования

![Image17](media/notebooks-guidance/image17.png)

Теперь тип markdown и вы увидите предварительной версии, в то же время

![Image18](media/notebooks-guidance/image18.png)

Нажмите кнопку **Запустить**. Приложение будет запущено Spark создает сеанс Spark как **spark** и определяет **HelloWorld** объекта.

Записная книжка должна выглядеть как на следующем рисунке.

Щелкнув за пределами ячейки, текст изменится на режим предварительного просмотра и скрывает markdown.

![Image19](media/notebooks-guidance/image19.png)


## <a name="manage-packages"></a>Управление пакетами
Одной из вещей, которые мы оптимизировали для локальной разработки Python было включают возможность установить пакеты, которые клиенты понадобится для своих сценариев. По умолчанию, мы включаем общие пакеты, такие как `pandas`, `numpy` и т.д., но если вы предполагаете, пакет, который не был включен затем написать следующий код в ячейку записной книжки: 

```python
import <package-name>
```

При выполнении этой команды `Module not found` возвращается. Если пакет существует, то не будет ошибка.

Если он возвращает `Module not Found` ошибки, а затем щелкните **управление пакетами** для запуска терминала на путь для вашей Virtualenv определены. Теперь можно установить пакеты локально. Чтобы установить пакеты, используйте следующие команды:

```bash
./pip install <package-name>
```

После установки пакета вы сможете перейдите в ячейку записной книжки и введите следующую команду:

```python
import <package-name>
```

Чтобы удалить пакет, используйте следующую команду из терминала:

```bash
./pip uninstall <package-name>
```

## <a name="next-steps"></a>Следующие шаги

Чтобы научиться работать с существующую записную книжку, см. в разделе [управление записных книжек в Azure Data Studio](notebooks-how-to-manage.md).