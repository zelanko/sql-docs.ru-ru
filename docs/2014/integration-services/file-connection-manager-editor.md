---
title: Редактор диспетчера подключения файлов | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.fileconnectionmanager.f1
helpviewer_keywords:
- File Connection Manager Editor
ms.assetid: 051c48e5-3d86-49af-b554-ff62e3de3622
caps.latest.revision: 22
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 0691e6d8b6bebec04d2126bba0caa8b14ed3cdd1
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37311944"
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
  
  
