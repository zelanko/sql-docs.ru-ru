---
title: Редактор диспетчера подключения файлов | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.fileconnectionmanager.f1
helpviewer_keywords:
- File Connection Manager Editor
ms.assetid: 051c48e5-3d86-49af-b554-ff62e3de3622
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 24793c3edc681ac40ca37c36a1540f3c404b7191
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2019
ms.locfileid: "58374832"
---
# <a name="file-connection-manager-editor"></a>редактор диспетчера подключения файлов
  Диалоговое окно **Редактор диспетчера подключения файлов** задает свойства, используемые при подключении к файлу или папке.  
  
> [!NOTE]  
>  Можно задать свойство ConnectionString для диспетчера соединений с файлами, указывая выражение в окне "Свойства" [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. Но чтобы избежать ошибки проверки при использовании выражения для указания файла или папки, добавьте путь к файлу или папке в пункте **Файл/папка**в **Редакторе диспетчера подключения файлов**.  
  
 Дополнительные сведения о диспетчере подключения файлов см. в разделе [File Connection Manager](connection-manager/file-connection-manager.md).  
  
## <a name="options"></a>Параметры  
 **Тип применения**  
 Укажите, будет ли **Диспетчер подключения файлов** подключаться к существующему файлу или папке или создаст новый файл или папку.  
  
|Значение|Описание|  
|-----------|-----------------|  
|Создать файл|Во время выполнения создается новый файл.|  
|Существующий файл|Использовать существующий файл.|  
|Создать папку|Во время выполнения создается новая папка.|  
|Существующая папка|Использовать существующую папку.|  
  
 **Файл / Папка**  
 Если **Файл**, укажите нужный файл.  
  
 Если **Папка**, укажите нужную папку.  
  
 **Обзор**  
 Выберите файл или папку в диалоговом окне **Выбор файла** или **Выбор папки** .  
  
## <a name="see-also"></a>См. также  
 [Справочник по сообщениям об ошибках служб Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  
