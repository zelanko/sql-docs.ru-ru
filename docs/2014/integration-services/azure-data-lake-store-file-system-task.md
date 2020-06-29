---
title: Задача "Файловая система" для Azure Data Lake Store | Документы Майкрософт
ms.custom: ''
ms.date: 01/09/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL12.DTS.DESIGNER.AFPADLSTASK.F1
- SQL11.DTS.DESIGNER.AFPADLSTASK.F1
ms.assetid: 02b9edd7-6ef9-463e-abbf-e1830bcae875
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2d01c61521bf746076b359c65103e0ea46ec0f1b
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/26/2020
ms.locfileid: "85439411"
---
# <a name="azure-data-lake-store-file-system-task"></a>Задача "Файловая система" для Azure Data Lake Store

**Задача "файловая система" Azure Data Lake Store** позволяет пользователям выполнять различные операции с файловой системой на [Azure Data Lake Store (ADLS)](https://azure.microsoft.com/services/data-lake-store/).

Чтобы добавить в пакет задачу "Файловая система" для Azure Data Lake Store, перетащите ее с панели элементов служб SSIS на панель холста конструктора. Дважды щелкните задачу или щелкните ее правой кнопкой мыши и выберите **изменить**, чтобы открыть диалоговое окно Редактор задачи.

Операция файловой системы, которая будет выполнена, задается свойством **Операция**. Поддерживаются следующие операции:

* **CopyToADLS**. Загрузка файлов в ADLS.
* **CopyFromADLS**. Скачивание файлов из ADLS.

Для любой операции необходимо указать диспетчер подключений Azure Data Lake.

Ниже приведены описания свойств, характерных для каждой операции.

## <a name="copytoadls"></a>CopyToADLS

* **LocalDirectory:** Указывает исходный каталог, содержащий файлы для отправки.
* **FileNamePattern**. Определяет фильтр имен для исходных файлов. Будут отправлены только те файлы, имя которых соответствует указанному шаблону. Поддерживаются подстановочные знаки `*` и `?`.
* **SearchRecursively**. Указывает, следует ли выполнять рекурсивный поиск файлов для загрузки в каталоге источника.
* **AzureDataLakeDirectory**. Указывает каталог назначения ADLS, в который будут загружены файлы.
* **Филикспири:** Указывает дату и время истечения срока действия файлов, отправленных в ADLS, или оставьте это свойство пустым, чтобы указать, что срок действия файлов никогда не истечет.

## <a name="copyfromadls"></a>CopyFromADLS

* **AzureDataLakeDirectory**. Указывает каталог источника ADLS, в котором содержатся файлы для скачивания.
* **SearchRecursively**. Указывает, следует ли выполнять рекурсивный поиск файлов для скачивания в каталоге источника.
* **LocalDirectory**. Указывает каталог назначения, в который будут сохранены скачанные файлы.
