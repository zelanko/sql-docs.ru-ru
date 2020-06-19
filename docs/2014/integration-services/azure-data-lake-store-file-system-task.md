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
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 30002ff43f841aa52ed809f217d3549cc64a768b
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84925363"
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
