---
title: "Задача передачи BLOB-объектов Azure | Документы Microsoft"
ms.custom: 
ms.date: 07/25/2016
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: control-flow
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.afpblobuptask.f1
- sql14.dts.designer.afpblobuptask.f1
ms.assetid: 6ea068b0-4cd8-45b5-b89d-09b8f25040c0
caps.latest.revision: 14
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: cec51398ac521abc0345e90b3c6ed156b542b5f1
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="azure-blob-upload-task"></a>Задача передачи больших двоичных объектов Azure
**Задача передачи BLOB-объектов Azure** позволяет пакету служб SSIS передавать файлы в хранилище BLOB-объектов Azure.
    
Чтобы добавить **задачу передачи BLOB-объектов Azure**, перетащите ее в конструктор служб SSIS и дважды щелкните или щелкните правой кнопкой мыши, а затем выберите **Изменить** , чтобы открыть диалоговое окно **Редактор задач передачи BLOB-объектов Azure** .  
  
 **Задача передачи BLOB-объектов Azure** — это компонент [пакет дополнительных компонентов SQL Server Integration Services (SSIS) для Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).
  
 Следующая таблица содержит описания полей этого диалогового окна.  
  
|||  
|-|-|  
|**Поле**|**Description**|  
|AzureStorageConnection|Создайте новый или укажите существующий диспетчер подключений службы хранилища Azure, который ссылается на учетную запись хранения Azure, указывающую на место размещения файлов BLOB-объектов.|  
|BlobContainer|Задает имя контейнера BLOB-объект, который содержит переданные файлы в виде больших двоичных объектов.|  
|BlobDirectory|Указывает каталог больших двоичных объектов, где загруженный файл хранится как большой двоичный объект блока. Каталог больших двоичных объектов — это виртуальная иерархическая структура. Если большой двоичный объект уже существует, он заменяется.|  
|LocalDirectory|Укажите локальный каталог, который содержит файлы для отправки.|  
|FileName|Указывает фильтр имен для выбора файлов с указанным шаблоном имен. Например `MySheet*.xls\*` содержит файлы, такие как `MySheet001.xls` и `MySheetABC.xlsx`.|  
|TimeRangeFrom/TimeRangeTo|Указывает фильтр по диапазону времени. Файлы, измененные после **TimeRangeFrom** и перед **TimeRangeTo** включены.|  
  
  

