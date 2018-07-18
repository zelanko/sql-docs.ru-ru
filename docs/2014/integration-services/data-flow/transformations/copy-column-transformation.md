---
title: Преобразование "Копирование столбца" | Документы Майкрософт
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
- sql12.dts.designer.copycolumntrans.f1
helpviewer_keywords:
- columns [Integration Services], copying
- copying columns
- Copy Column transformation
ms.assetid: 1c72a313-9026-46bc-a57f-c6b3f47346f8
caps.latest.revision: 36
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 6bd1ef03d1a45151e6f81d46b15e4e7fbc19f9a2
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37261470"
---
# <a name="copy-column-transformation"></a>преобразование «Копирование столбца»
  Преобразование «Копирование столбца» позволяет создавать новые столбцы путем копирования входных столбцов и добавления новых к выходу преобразования. На более поздних этапах потока данных к копиям столбцов могут применяться различные преобразования. Например, преобразование «Копирование столбца» можно использовать для создания копии столбца и дальнейшего перевода символов скопированных данных в верхний регистр с помощью преобразования «Таблица символов» или для статистической обработки нового столбца с помощью преобразования «Агрегатная обработка».  
  
## <a name="configuration-of-the-copy-column-transformation"></a>Настройка преобразования «Копирование столбца»  
 Преобразование «Копирование столбца» настраивается путем определения входных столбцов, которые необходимо скопировать. Можно создать несколько копий столбца или же копии нескольких столбцов в одной операции.  
  
 Это преобразование имеет один вход и один выход. Вывод ошибок не поддерживается.  
  
 Свойства могут устанавливаться через конструктор служб [!INCLUDE[ssIS](../../../includes/ssis-md.md)] или с помощью программных средств.  
  
 Дополнительные сведения о свойствах, которые можно установить в диалоговом окне **Редактор преобразования «Копирование столбцов»** , см. в разделе [Copy Column Transformation Editor](../../copy-column-transformation-editor.md).  
  
 Диалоговое окно **Расширенный редактор** содержит свойства, которые можно установить с помощью программных средств. Дополнительные сведения о свойствах, которые вы можете задать в диалоговом окне **Расширенный редактор** или программными средствами, см. в следующих разделах.  
  
-   [Общие свойства](../../common-properties.md)  
  
-   [Пользовательские свойства преобразований](transformation-custom-properties.md)  
  
 Дополнительные сведения о настройке свойств см. в разделе [Установление свойств компонента потока данных](../set-the-properties-of-a-data-flow-component.md).  
  
## <a name="see-also"></a>См. также  
 [Поток данных](../data-flow.md)   
 [Преобразования служб Integration Services](integration-services-transformations.md)  
  
  
