---
title: Задача скачивания BLOB-объектов Azure | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.afpblobdltask.f1
- sql11.dts.designer.afpblobdltask.f1
ms.assetid: 8a63bf44-71be-456d-9a5c-be7c31aff065
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e2f61260b1fceaad3c27a0ce6ab6af28b15582bc
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/26/2020
ms.locfileid: "85433981"
---
# <a name="azure-blob-download-task"></a>Задача скачивания BLOB-объектов Azure
  Задача скачивания BLOB-объектов Azure позволяет пакету служб SSIS скачивать файлы из хранилища BLOB-объектов Azure.   
Чтобы добавить **задачу скачивания BLOB-объектов Azure**, перетащите ее в конструкторе служб SSIS и дважды щелкните или щелкните правой кнопкой мыши и выберите **Изменить** , чтобы вызвать диалоговое окно **Редактор задач скачивания BLOB-объектов Azure** .  
  
 Следующая таблица содержит описание полей этого диалогового окна.  
  
|||  
|-|-|  
|**Поле**|**Описание**|  
|AzureStorageConnection|Создайте новый или укажите существующий диспетчер подключений службы хранилища Azure, который ссылается на учетную запись хранения Azure, указывающую на место размещения файлов BLOB-объектов.|  
|BlobContainer|Указывает имя контейнера BLOB-объектов, который содержит скачиваемые файлы BLOB-объектов.|  
|BlobDirectory|Указывает каталог больших двоичных объектов, который содержит скачиваемые файлы BLOB-объектов. Каталог больших двоичных объектов — это виртуальная иерархическая структура.|  
|LocalDirectory|Указывает локальный каталог для хранения скачанных файлов BLOB-объектов.|  
|FileName|Указывает имя фильтра для выбора файлов с указанным шаблоном имени. Пример: MySheet*.xls\* включает такие файлы, как MySheet001.xls и MySheetABC.xlsx.|  
|TimeRangeFrom/TimeRangeTo|Задает фильтр диапазона времени. Будут включены файлы, измененные после **TimeRangeFrom** и до **TimeRangeTo** .|  
  
  
