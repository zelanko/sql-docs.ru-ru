---
title: Задача "Файловая система" для Azure Data Lake Store | Документы Майкрософт
ms.custom: ''
ms.date: 01/09/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- SQL12.DTS.DESIGNER.AFPADLSTASK.F1
- SQL11.DTS.DESIGNER.AFPADLSTASK.F1
ms.assetid: 02b9edd7-6ef9-463e-abbf-e1830bcae875
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: aeabdcfa1fd36adf9bd4291623c56fbfecf0520e
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2019
ms.locfileid: "58390252"
---
# <a name="azure-data-lake-store-file-system-task"></a>Задача "Файловая система" для Azure Data Lake Store

**Azure Data Lake Store File System Task** дает пользователям возможность выполнять различные операции файловой системы на [Azure Data Lake Store (ADLS)](https://azure.microsoft.com/services/data-lake-store/).

Чтобы добавить в пакет задачу "Файловая система" для Azure Data Lake Store, перетащите ее с панели элементов служб SSIS на панель холста конструктора. Затем дважды щелкните задачу, или щелкните правой кнопкой мыши задачу и выберите **изменить**, чтобы открыть диалоговое окно редактора задач.

Операция файловой системы, которая будет выполнена, задается свойством **Операция**. Поддерживаются следующие операции.

* **CopyToADLS:** Загрузка файлов в ADLS.
* **CopyFromADLS:** Скачивание файлов из ADLS.

Для любой операции необходимо указать диспетчер подключений Azure Data Lake.

Ниже приведены описания свойств, относящиеся к каждой операции.

## <a name="copytoadls"></a>CopyToADLS

* **LocalDirectory:** Указывает исходный каталог, в котором содержатся файлы для загрузки.
* **FileNamePattern:** Указывает фильтр имен для исходных файлов. Будут отправлены только файлы, имя которого соответствует указанному шаблону. Поддерживаются подстановочные знаки `*` и `?`.
* **SearchRecursively:** Указывает, следует ли выполнять рекурсивный поиск в исходный каталог для файлов для отправки.
* **AzureDataLakeDirectory:** Указывает каталог назначения ADLS отправке файлов.
* **FileExpiry:** Указывает срок действия и время для файлов, загруженных в ADLS, или оставьте это свойство пустым, чтобы указать, что файлы никогда не истекает.

## <a name="copyfromadls"></a>CopyFromADLS

* **AzureDataLakeDirectory:** Указывает каталог источника ADLS, которая содержит файлы для загрузки.
* **SearchRecursively:** Указывает, следует ли выполнять рекурсивный поиск в исходный каталог для файлов для загрузки.
* **LocalDirectory:** Указывает каталог назначения, чтобы сохранить загруженные файлы.
