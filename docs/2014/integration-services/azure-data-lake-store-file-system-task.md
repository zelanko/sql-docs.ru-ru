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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66061379"
---
# <a name="azure-data-lake-store-file-system-task"></a>Задача "Файловая система" для Azure Data Lake Store

**Задача "файловая система" Azure Data Lake Store** позволяет пользователям выполнять различные операции с файловой системой на [Azure Data Lake Store (ADLS)](https://azure.microsoft.com/services/data-lake-store/).

Чтобы добавить в пакет задачу "Файловая система" для Azure Data Lake Store, перетащите ее с панели элементов служб SSIS на панель холста конструктора. Дважды щелкните задачу или щелкните ее правой кнопкой мыши и выберите **изменить**, чтобы открыть диалоговое окно Редактор задачи.

Операция файловой системы, которая будет выполнена, задается свойством **Операция**. Поддерживаются следующие операции:

* **Копитоадлс:** Отправка файлов в ADLS.
* **Копифромадлс:** Скачивание файлов из ADLS.

Для любой операции необходимо указать диспетчер подключений Azure Data Lake.

Ниже приведены описания свойств, характерных для каждой операции.

## <a name="copytoadls"></a>CopyToADLS

* **LocalDirectory:** Указывает исходный каталог, содержащий файлы для отправки.
* **Филенамепаттерн:** Задает фильтр имен файлов для исходных файлов. Будут отправлены только те файлы, имя которых соответствует указанному шаблону. Поддерживаются подстановочные знаки `*` и `?`.
* **SearchRecursively:** Указывает, следует ли выполнять рекурсивный поиск загружаемых файлов в исходном каталоге.
* **AzureDataLakeDirectory:** Указывает целевой каталог ADLS для отправки файлов.
* **Филикспири:** Указывает дату и время истечения срока действия файлов, отправленных в ADLS, или оставьте это свойство пустым, чтобы указать, что срок действия файлов никогда не истечет.

## <a name="copyfromadls"></a>CopyFromADLS

* **AzureDataLakeDirectory:** Указывает исходный каталог ADLS, содержащий файлы для загрузки.
* **SearchRecursively:** Указывает, следует ли выполнять рекурсивный поиск загружаемых файлов в исходном каталоге.
* **LocalDirectory:** Указывает целевой каталог для хранения скачанных файлов.
