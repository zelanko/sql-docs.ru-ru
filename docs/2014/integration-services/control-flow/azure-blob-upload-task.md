---
title: Задача передачи больших двоичных объектов Azure | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.afpblobuptask.f1
- sql11.dts.designer.afpblobuptask.f1
ms.assetid: 6ea068b0-4cd8-45b5-b89d-09b8f25040c0
caps.latest.revision: 12
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d0f0e4123a16eb82000c6506dc7bcb62b353a268
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37188561"
---
# <a name="azure-blob-upload-task"></a>Задача передачи больших двоичных объектов Azure
  Задача передачи BLOB-объектов Azure позволяет пакету служб SSIS передавать файлы в хранилище BLOB-объектов Azure.   
Чтобы добавить **задачу передачи BLOB-объектов Azure**, перетащите ее в конструктор служб SSIS и дважды щелкните или щелкните правой кнопкой мыши, а затем выберите **Изменить** , чтобы открыть диалоговое окно **Редактор задач передачи BLOB-объектов Azure** .  
  
 Следующая таблица содержит описания полей этого диалогового окна.  
  
|||  
|-|-|  
|**Поле**|**Описание**|  
|AzureStorageConnection|Создайте новый или укажите существующий диспетчер подключений службы хранилища Azure, который ссылается на учетную запись хранения Azure, указывающую на место размещения файлов BLOB-объектов.|  
|BlobContainer|Задает имя контейнера BLOB-объектов, который будет содержать переданные файлы в виде больших двоичных объектов.|  
|BlobDirectory|Указывает каталог больших двоичных объектов, где загруженный файл будет храниться в виде блочного BLOB-объекта. Каталог больших двоичных объектов — это виртуальная иерархическая структура. Если большой двоичный объект уже существует, он будет заменен.|  
|LocalDirectory|Укажите локальный каталог, который содержит файлы для отправки.|  
|FileName|Указывает фильтр имен для выбора файлов с указанным шаблоном имен. Пример: MySheet*.xls\* включает такие файлы, как MySheet001.xls и MySheetABC.xlsx.|  
|TimeRangeFrom/TimeRangeTo|Указывает фильтр по диапазону времени. Будут включены файлы, измененные после **TimeRangeFrom** и до **TimeRangeTo** .|  
  
  
