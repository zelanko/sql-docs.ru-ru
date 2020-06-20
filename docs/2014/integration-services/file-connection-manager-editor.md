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
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 9128f73dc8fec388ae111781b9beeb52bbab138b
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84967154"
---
# <a name="file-connection-manager-editor"></a>редактор диспетчера подключения файлов
  Диалоговое окно **Редактор диспетчера подключения файлов** задает свойства, используемые при подключении к файлу или папке.  
  
> [!NOTE]  
>  Можно задать свойство ConnectionString для диспетчера соединений с файлами, указывая выражение в окне "Свойства" [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. Но чтобы избежать ошибки проверки при использовании выражения для указания файла или папки, добавьте путь к файлу или папке в пункте **Файл/папка**в **Редакторе диспетчера подключения файлов**.  
  
 Дополнительные сведения о диспетчере подключения файлов см. в разделе [File Connection Manager](connection-manager/file-connection-manager.md).  
  
## <a name="options"></a>Варианты  
 **Тип использования**  
 Укажите, будет ли **Диспетчер подключения файлов** подключаться к существующему файлу или папке или создаст новый файл или папку.  
  
|Применение|Описание|  
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
  
## <a name="see-also"></a>См. также:  
 [Справочник по сообщениям об ошибках служб Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  
