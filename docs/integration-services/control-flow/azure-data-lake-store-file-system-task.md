---
title: "Задача файловой системы для хранилища Озера данных Azure | Документы Microsoft"
ms.custom: 
ms.date: 08/22/2017
ms.prod: sql-server-2016
ms.reviewer: douglasl
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SQL13.DTS.DESIGNER.AFPADLSTASK.F1
- SQL14.DTS.DESIGNER.AFPADLSTASK.F1
author: Lingxi-Li
ms.author: lingxl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 29122bdf543e82c1f429cf401b5fe1d8383515fc
ms.openlocfilehash: 4cb0585acf73e734662847401c60686b54ae6410
ms.contentlocale: ru-ru
ms.lasthandoff: 10/10/2017

---
# <a name="azure-data-lake-store-file-system-task"></a>Задача файловой системы для хранилища Озера данных Azure

Задача Azure хранилища Озера данных файла система позволяет пользователям выполнять различные операции файловой системы на [хранилища Озера данных Azure (ADLS)](https://azure.microsoft.com/services/data-lake-store/).

Задача Azure хранилища Озера данных файла системы — это компонент [пакет дополнительных компонентов SQL Server Integration Services (SSIS) для Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).

## <a name="configure-the-azure-data-lake-store-file-system-task"></a>Настройка хранилища Озера данных Azure File System Task

Чтобы добавить пакет Azure данных Озера хранилище File System Task, перетащите его из области элементов служб SSIS на полотно конструктора. Затем дважды щелкните задачу, или щелкните правой кнопкой мыши задачу и выберите **изменить**, чтобы открыть **Azure хранилища Озера данных файла редактор задачи системы** диалоговое окно.

**Операции** свойство указывает, для выполнения операции файловой системы. Выберите один из следующих операций:

- **CopyToADLS:** передачи файлов в ADLS.
- **CopyFromADLS:** загрузка файлов из ADLS.

Для любой операции необходимо указать диспетчер соединений Озера данных Azure.

Ниже приведены свойства, относящиеся к каждой операции.

### <a name="copytoadls"></a>CopyToADLS
- **LocalDirectory:** указывает каталог локального источника, содержащего файлов для отправки.
- **FileNamePattern:** указывает фильтр имен файлов для исходных файлов. Передаются только файлы, имя которого соответствует указанному шаблону. Подстановочные знаки `*` и `?` поддерживаются.
- **SearchRecursively:** указывает, следует ли выполнять поиск рекурсивно в исходный каталог для файлов для отправки.
- **AzureDataLakeDirectory:** указывает на отправку файлов в каталог назначения ADLS.
- **FileExpiry:** задает срок действия и время для файлов переданы ADLS. Оставьте это свойство пустым, чтобы указать, что файлы никогда не истекает.

### <a name="copyfromadls"></a>CopyFromADLS
- **AzureDataLakeDirectory:** указывает исходный каталог ADLS, которая содержит файлы для загрузки.
- **SearchRecursively:** указывает, следует ли выполнять поиск рекурсивно в исходный каталог для файлов для загрузки.
- **LocalDirectory:** указывает каталог назначения, чтобы сохранить загруженные файлы.
