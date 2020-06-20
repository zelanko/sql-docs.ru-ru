---
title: Преобразование "Копирование столбца" | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.copycolumntrans.f1
helpviewer_keywords:
- columns [Integration Services], copying
- copying columns
- Copy Column transformation
ms.assetid: 1c72a313-9026-46bc-a57f-c6b3f47346f8
author: janinezhang
ms.author: janinez
ms.openlocfilehash: d150aa7bcf77268cdfdbc3b037e28f358a115a97
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84939663"
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
  
-   [Transformation Custom Properties](transformation-custom-properties.md)  
  
 Дополнительные сведения о настройке свойств см. в разделе [Установление свойств компонента потока данных](../set-the-properties-of-a-data-flow-component.md).  
  
## <a name="see-also"></a>См. также:  
 [Поток данных](../data-flow.md)   
 [Преобразования служб Integration Services](integration-services-transformations.md)  
  
  
