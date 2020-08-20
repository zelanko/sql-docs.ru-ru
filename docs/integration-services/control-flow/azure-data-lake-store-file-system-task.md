---
description: Задача "Файловая система" для Azure Data Lake Store
title: Задача "Файловая система" для Azure Data Lake Store | Документы Майкрософт
ms.custom: ''
ms.date: 08/22/2017
ms.prod: sql
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL13.DTS.DESIGNER.AFPADLSTASK.F1
- SQL14.DTS.DESIGNER.AFPADLSTASK.F1
author: Lingxi-Li
ms.author: lingxl
ms.reviewer: maghan
ms.openlocfilehash: 27ee71393bfbad6c824de25bd95c9ca465cf2a51
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88496087"
---
# <a name="azure-data-lake-store-file-system-task"></a>Задача "Файловая система" для Azure Data Lake Store

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]



Задача "Файловая система" для Azure Data Lake Store позволяет пользователям выполнять различные операции файловой системы в [Azure Data Lake Store (ADLS)](https://azure.microsoft.com/services/data-lake-store/).

Компонент задачи "Файловая система" для Azure Data Lake Store входит в состав [пакета дополнительных компонентов SQL Server Integration Services (SSIS) для Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).

## <a name="configure-the-azure-data-lake-store-file-system-task"></a>Настройка задачи "Файловая система" для Azure Data Lake Store

Чтобы добавить в пакет задачу "Файловая система" для Azure Data Lake Store, перетащите ее с панели элементов служб SSIS на панель холста конструктора. Затем дважды щелкните задачу или щелкните ее правой кнопкой мыши и выберите команду **Изменить**, чтобы открыть диалоговое окно **редактора задачи "Файловая система" для Azure Data Lake Store**.

Операция файловой системы, которая будет выполнена, задается свойством **Операция**. Выберите одну из следующих операций:

- **CopyToADLS**. Загрузка файлов в ADLS.
- **CopyFromADLS**. Скачивание файлов из ADLS.

## <a name="configure-the-properties-for-the-operation"></a>Настройка свойств операции
Для любой операции необходимо указать диспетчер подключений Azure Data Lake.

Ниже приведены свойства, относящиеся к каждой операции:

### <a name="copytoadls"></a>CopyToADLS
- **LocalDirectory**. Задает каталог локального источника, в котором содержатся загружаемые файлы.
- **FileNamePattern**. Определяет фильтр имен для исходных файлов. Загружаются только те файлы, имя которых соответствует указанному шаблону. Поддерживаются подстановочные знаки `*` и `?`.
- **SearchRecursively**. Указывает, следует ли выполнять рекурсивный поиск файлов для загрузки в каталоге источника.
- **AzureDataLakeDirectory**. Указывает каталог назначения ADLS, в который будут загружены файлы.
- **FileExpiry**. Задает дату и время истечения срока действия для файлов, загруженных в ADLS. Если файлы не имеют срока действия, оставьте это свойство пустым.

### <a name="copyfromadls"></a>CopyFromADLS
- **AzureDataLakeDirectory**. Указывает каталог источника ADLS, в котором содержатся файлы для скачивания.
- **SearchRecursively**. Указывает, следует ли выполнять рекурсивный поиск файлов для скачивания в каталоге источника.
- **LocalDirectory**. Указывает каталог назначения, в который будут сохранены скачанные файлы.
