---
title: Как использовать записные книжки в предварительной версии SQL Server 2019 | Документация Майкрософт
description: ''
author: rothja
ms.author: jroth
manager: craigg
ms.date: 11/06/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: 9f9db16431cd6c3befbb32383725ec008f5a9081
ms.sourcegitcommit: cb73d60db8df15bf929ca17c1576cf1c4dca1780
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2018
ms.locfileid: "51221640"
---
# <a name="how-to-use-notebooks-in-sql-server-2019-preview"></a>Как использовать записные книжки в предварительной версии SQL Server 2019

В этой статье описывается, как запустить записные книжки Jupyter в кластере и разработке собственных записных книжек. Также показано, как отправлять задания, к кластеру.

## <a name="prerequisites"></a>предварительные требования

Использовать записные книжки, необходимо установить следующие компоненты:

- [Кластер SQL Server 2019 больших данных](deployment-guidance.md)
- [Azure Data Studio](../azure-data-studio/what-is.md)
- [Расширение SQL Server 2019 (Предварительная версия)](../azure-data-studio/sql-server-2019-extension.md).

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a name="connect-to-the-hadoop-gateway-knox-end-point"></a>Подключение к конечной точки шлюза Knox Hadoop

Вы можете подключиться к разные конечные точки в кластере. Можно подключиться к типу соединения Microsoft SQL Server или в конечную точку шлюза HDFS или Spark.
В студии данных Azure (Предварительная версия), нажмите клавишу F1 и нажмите кнопку **новое подключение** и вы можете подключиться к вашей конечной точки шлюза HDFS или Spark.

![изображение 1](media/notebooks-guidance/image1.png)

## <a name="browse-hdfs"></a>Обзор HDFS

После подключения вы сможете просмотреть папку HDFS. WebHDFS запускается после завершения развертывания, и вы сможете для **обновить**, добавьте **новый каталог**, **отправить** файлы, и **удалить**.

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

  Например, введите имя записной книжки, `Test.ipynb`. Нажмите кнопку **Сохранить**.

![image6](media/notebooks-guidance/image6.png)

## <a name="supported-kernels-and-attach-to-context"></a>Поддерживаемые версии ядра и присоединить к контексту

Установка записной книжки поддерживает ядрами PySpark и Spark, волшебной команды Spark, которые позволяют писать код Python и Scala, с помощью Spark. При необходимости можно выбрать Python целях локальной разработки.

![image7](media/notebooks-guidance/image7.png)

При выборе одного из этих ядер, мы установим этот ядра в виртуальной среде и написания кода на поддерживаемых языках.

|Ядра|Описание
|:-----|:-----
|Ядро PySpark|Для написания кода Python, с помощью Spark вычислений из кластера.
|Ядро Spark|Для написания кода Scala, с помощью Spark вычислений из кластера.
|Ядро Python|Для написания кода Python для локальной разработки.

`Attach to` Предоставляет контекст для ядра для присоединения. Когда вы подключены и заканчивая шлюза HDFS или Spark (Knox) выберите значение по умолчанию `Attach to` является конечной точки кластера.

![image8](media/notebooks-guidance/image8.png)

## <a name="hello-world-in-different-contexts"></a>Hello world в различных контекстах

### <a name="pyspark-kernel"></a>Ядро Pyspark

Выберите ядро PySpark и в тип ячейки в следующем коде:

![image9](media/notebooks-guidance/image9.png)

Щелкните выполнения и вам следует см. запуск приложения Spark и вы увидите следующие выходные данные:

![Image10](media/notebooks-guidance/image10.png)

Результат должен выглядеть примерно так, как на рисунке ниже.

![Image11](media/notebooks-guidance/image11.png)

### <a name="spark-kernel"></a>Ядро Spark
Добавьте новую ячейку кода, нажав кнопку **+ Code** команды на панели инструментов.

![Image12](media/notebooks-guidance/image12.png)

Вы также можете просмотреть «Параметры ячейки», при нажатии на значок "Параметры" ниже.

![Image13](media/notebooks-guidance/image13.png)

Ниже приведены параметры для каждой клетки.

![Image14](media/notebooks-guidance/image14.png)-

Теперь выберите ядро Spark, в раскрывающемся списке для ядра, а также в ячейке введите или вставьте в —

![Image15](media/notebooks-guidance/image15.png)

Нажмите кнопку **запуска** и вы увидите запуск приложения Spark, и это создает сеанс Spark как **spark** и определяете **HelloWorld** объекта.

Записная книжка должна выглядеть как на следующем рисунке.

![Image16](media/notebooks-guidance/image16.png)

Определив объект затем в следующей ячейке записной книжки, введите следующий код:

![Image17](media/notebooks-guidance/image17.png)

Нажмите кнопку **запуска** в записной книжке меню и вы увидите «Hello, world!» в выходных данных.

![Image18](media/notebooks-guidance/image18.png)

### <a name="local-python-kernel"></a>Ядро локального python
Выберите локальное ядро Python и в тип ячейки в -

![Image19](media/notebooks-guidance/image19.png)

Вы должны увидеть следующие выходные данные:

![Image20](media/notebooks-guidance/image20.png)

### <a name="markdown-text"></a>Текст с разметкой markdown
Добавьте новую ячейку текст, нажав кнопку **+ текст** команды на панели инструментов.

![Image21](media/notebooks-guidance/image21.png)

Щелкните значок предварительного просмотра, чтобы добавить markdown

![Image22](media/notebooks-guidance/image22.png)

Щелкните значок предварительного просмотра еще раз, чтобы переключиться на просмотр просто markdown

![Image23](media/notebooks-guidance/image23.png)

## <a name="manage-packages"></a>Управление пакетами
Одной из вещей, которые мы оптимизировали для локальной разработки Python было включают возможность установить пакеты, которые клиенты понадобится для своих сценариев. По умолчанию, мы включаем общие пакеты, как pandas, numpy и т.д., но если вы предполагаете, пакет, который не был включен затем написать следующий код в ячейку записной книжки: 

```python
import <package-name>
```

При выполнении этой команды вы получите `Module not found` ошибки. Если пакет существует, то не будет ошибка.

Если вы нашли `Module not Found` ошибки, а затем щелкните **управление пакетами** для запуска терминала на путь для вашей Virtualenv определены. Теперь можно установить пакеты локально. Чтобы установить пакеты, используйте следующие команды:

```bash
./pip install <package-name>
```

После установки пакета вы сможете перейдите в ячейку записной книжки и введите следующую команду:

```python
import <package-name>
```

Теперь при выполнении ячейки, вы больше не должны получить `Module not found` ошибки.

Чтобы удалить пакет, используйте следующую команду из терминала:

```bash
./pip uninstall <package-name>
```

## <a name="next-steps"></a>Следующие шаги

Чтобы научиться работать с существующую записную книжку, см. в разделе [управление записных книжек в Azure Data Studio](notebooks-how-to-manage.md).