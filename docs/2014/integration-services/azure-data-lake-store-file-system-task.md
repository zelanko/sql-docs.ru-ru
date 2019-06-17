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
manager: craigg
ms.openlocfilehash: 69a521cb72e68141f5706f5187a0288a3f44f241
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66061379"
---
# <a name="azure-data-lake-store-file-system-task"></a>Задача "Файловая система" для Azure Data Lake Store

**Azure Data Lake Store File System Task** дает пользователям возможность выполнять различные операции файловой системы на [Azure Data Lake Store (ADLS)](https://azure.microsoft.com/services/data-lake-store/).

Чтобы добавить в пакет задачу "Файловая система" для Azure Data Lake Store, перетащите ее с панели элементов служб SSIS на панель холста конструктора. Затем дважды щелкните задачу, или щелкните правой кнопкой мыши задачу и выберите **изменить**, чтобы открыть диалоговое окно редактора задач.

Операция файловой системы, которая будет выполнена, задается свойством **Операция**. Поддерживаются следующие операции.

* **CopyToADLS.** Загрузка файлов в ADLS.
* **CopyFromADLS.** Скачивание файлов из ADLS.

Для любой операции необходимо указать диспетчер подключений Azure Data Lake.

Ниже приведены описания свойств, относящиеся к каждой операции.

## <a name="copytoadls"></a>CopyToADLS

* **LocalDirectory.** Указывает исходный каталог, в котором содержатся файлы для загрузки.
* **FileNamePattern.** Определяет фильтр имен для исходных файлов. Будут отправлены только файлы, имя которого соответствует указанному шаблону. Поддерживаются подстановочные знаки `*` и `?`.
* **SearchRecursively.** Указывает, следует ли выполнять рекурсивный поиск файлов для загрузки в каталоге источника.
* **AzureDataLakeDirectory.** Определяет каталог назначения ADLS, в который будут загружены файлы.
* **FileExpiry.** Указывает срок действия и время для файлов, загруженных в ADLS, или оставьте это свойство пустым, чтобы указать, что файлы никогда не истекает.

## <a name="copyfromadls"></a>CopyFromADLS

* **AzureDataLakeDirectory.** Определяет каталог источника ADLS, в котором содержатся файлы для скачивания.
* **SearchRecursively.** Определяет, следует ли выполнять рекурсивный поиск файлов для скачивания в каталоге источника.
* **LocalDirectory.** Определяет каталог назначения, в котором будут сохранены скачанные файлы.
