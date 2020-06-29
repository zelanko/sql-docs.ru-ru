---
title: Редактор диспетчера подключения файлов | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.fileconnectionmanager.f1
helpviewer_keywords:
- File Connection Manager Editor
ms.assetid: 051c48e5-3d86-49af-b554-ff62e3de3622
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5ae883d085b1f6416096255a3b87d6e5872bc5e9
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/26/2020
ms.locfileid: "85425711"
---
# <a name="file-connection-manager-editor"></a>редактор диспетчера подключения файлов
  Диалоговое окно **Редактор диспетчера подключения файлов** задает свойства, используемые при подключении к файлу или папке.  
  
> [!NOTE]  
>  Можно задать свойство ConnectionString для диспетчера соединений с файлами, указывая выражение в окне "Свойства" [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. Но чтобы избежать ошибки проверки при использовании выражения для указания файла или папки, добавьте путь к файлу или папке в пункте **Файл/папка**в **Редакторе диспетчера подключения файлов**.  
  
 Дополнительные сведения о диспетчере подключения файлов см. в разделе [File Connection Manager](connection-manager/file-connection-manager.md).  
  
## <a name="options"></a>Параметры  
 **Тип использования**  
 Укажите, будет ли **Диспетчер подключения файлов** подключаться к существующему файлу или папке или создаст новый файл или папку.  
  
|Значение|Описание:|  
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
  
  
