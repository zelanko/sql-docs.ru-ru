---
title: "Задача файловой системы для хранилища Озера данных Azure | Документы Microsoft"
ms.custom: 
ms.date: 08/22/2017
ms.prod: sql-server-2016
ms.reviewer: 
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
ms.sourcegitcommit: 303d3b74da3fe370d19b7602c0e11e67b63191e7
ms.openlocfilehash: ce2355de312faed9ab66991d6d0dd344ff315a55
ms.contentlocale: ru-ru
ms.lasthandoff: 08/29/2017

---
# <a name="azure-data-lake-store-file-system-task"></a>Задача файловой системы для хранилища Озера данных Azure

**Azure Озера данных хранилище File System Task** дает пользователям возможность выполнять различные операции файловой системы на [хранилища Озера данных Azure (ADLS)](https://azure.microsoft.com/services/data-lake-store/).

**Azure Озера данных хранилище File System Task** — это компонент [пакет дополнительных компонентов SQL Server Integration Services (SSIS) для Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).

Чтобы добавить пакет Azure данных Озера хранилище File System Task, перетащите его из области элементов служб SSIS на полотно конструктора. Затем дважды щелкните задачу, или щелкните правой кнопкой мыши задачу и выберите **изменить**, чтобы открыть диалоговое окно редактора задачи.

**Операции** свойство указывает, для выполнения операции файловой системы. Поддерживаются следующие операции.

* **CopyToADLS:** передачи файлов в ADLS.
* **CopyFromADLS:** загрузка файлов из ADLS.

Для любой операции необходимо указать диспетчер соединений Озера данных Azure.

Ниже приведены описания свойств для каждой операции.

## <a name="copytoadls"></a>CopyToADLS
* **LocalDirectory:** указывает исходный каталог, который содержит файлы для загрузки.
* **FileNamePattern:** указывает фильтр имен файлов для исходных файлов. Будет загружен только файлы, имя которого соответствует указанному шаблону. Подстановочные знаки `*` и `?` поддерживаются.
* **SearchRecursively:** указывает, следует ли выполнять поиск рекурсивно в исходный каталог для файлов для отправки.
* **AzureDataLakeDirectory:** указывает на отправку файлов в каталог назначения ADLS.
* **FileExpiry:** задает срок действия и время для файлов, отправки ADLS, или оставьте это свойство пустым, чтобы указать, что файлы никогда не истекает.

## <a name="copyfromadls"></a>CopyFromADLS
* **AzureDataLakeDirectory:** указывает исходный каталог ADLS, которая содержит файлы для загрузки.
* **SearchRecursively:** указывает, следует ли выполнять поиск рекурсивно в исходный каталог для файлов для загрузки.
* **LocalDirectory:** указывает каталог назначения, чтобы сохранить загруженные файлы.
