---
title: Задача скачивания BLOB-объектов Azure | Документы Майкрософт
ms.custom: ''
ms.date: 05/22/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.afpblobdltask.f1
- sql14.dts.designer.afpblobdltask.f1
ms.assetid: 8a63bf44-71be-456d-9a5c-be7c31aff065
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: ec05684572563228ec3bce88ebb5c5ca32a86bc2
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66403194"
---
# <a name="azure-blob-download-task"></a>Задача скачивания BLOB-объектов Azure

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


Задача скачивания BLOB-объектов Azure позволяет пакету служб SSIS скачивать файлы из хранилища BLOB-объектов Azure.

Чтобы добавить **задачу скачивания BLOB-объектов Azure**, перетащите ее в конструкторе служб SSIS и дважды щелкните или щелкните правой кнопкой мыши и выберите **Изменить** , чтобы вызвать диалоговое окно **Редактор задач скачивания BLOB-объектов Azure** .  
  
 **Задача скачивания BLOB-объектов Azure** входит в состав [пакета дополнительных компонентов SQL Server Integration Services (SSIS) для Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).  
  
 Следующая таблица содержит описание полей этого диалогового окна.  

|**Поле**|**Описание**|  
|---|---|
|AzureStorageConnection|Создайте новый или укажите существующий диспетчер подключений службы хранилища Azure, который ссылается на учетную запись хранения Azure, указывающую на место размещения файлов BLOB-объектов.|  
|BlobContainer|Указывает имя контейнера BLOB-объектов, который содержит скачиваемые файлы BLOB-объектов.|  
|BlobDirectory|Указывает каталог больших двоичных объектов, который содержит скачиваемые файлы BLOB-объектов. Каталог больших двоичных объектов — это виртуальная иерархическая структура.|  
|SearchRecursively|Указывает, следует ли выполнять рекурсивный поиск в подкаталогах.|  
|LocalDirectory|Указывает локальный каталог для хранения скачанных файлов BLOB-объектов.|  
|FileName|Указывает фильтр имен для выбора файлов с указанным шаблоном имен. Например, `MySheet*.xls\*` включает такие файлы, как `MySheet001.xls` и `MySheetABC.xlsx`.|  
|TimeRangeFrom/TimeRangeTo|Указывает фильтр по диапазону времени. Включаются файлы, измененные после **TimeRangeFrom** и до **TimeRangeTo**.|  
