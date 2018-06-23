---
title: Задача скачивания BLOB-объектов Azure | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.afpblobdltask.f1
- sql11.dts.designer.afpblobdltask.f1
ms.assetid: 8a63bf44-71be-456d-9a5c-be7c31aff065
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 680d2efd5d2f5cbc52539c0340539d33f1c6bcb3
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36190495"
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
|FileName|Указывает фильтр имен для выбора файлов с указанным шаблоном имен. Пример: MySheet*.xls\* включает такие файлы, как MySheet001.xls и MySheetABC.xlsx.|  
|TimeRangeFrom/TimeRangeTo|Указывает фильтр по диапазону времени. Будут включены файлы, измененные после **TimeRangeFrom** и до **TimeRangeTo** .|  
  
  