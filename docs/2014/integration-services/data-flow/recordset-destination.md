---
title: Назначение "Набора записей" | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.recordsetdest.f1
helpviewer_keywords:
- Recordset destination
- ADO recordsets [Integration Services]
- destinations [Integration Services], Recordset
- in-memory ADO recordsets [Integration Services]
ms.assetid: be973cf1-c4ff-49f8-987e-314c08ef98e4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c1acc29c904e9020721e8ac62dff09a8ec29a392
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/26/2020
ms.locfileid: "85431491"
---
# <a name="recordset-destination"></a>назначение «Набор записей»
  Назначение «Набора записей» создает и заполняет набор записей ADO в памяти. Форма набора записей определяется входными данными назначения «набор записей» во время проектирования.  
  
## <a name="configuration-of-the-recordset-destination"></a>Настройка назначения «Набор записей»  
 Назначение «Набор записей» настраивается с помощью указания переменной для хранения набора записей ADO.  
  
 Во время выполнения набор записей ADO записывается в переменную типа Object, заданную в свойстве VariableName назначения "Набор записей". Переменная делает набор записей доступным за пределами потока данных, где он может быть использован скриптами и другими элементами пакета.  
  
 У данного источника один вход. Вывод ошибок не поддерживается.  
  
 Значения свойств можно задавать с помощью конструктора [!INCLUDE[ssIS](../../includes/ssis-md.md)] или программными средствами.  
  
 Диалоговое окно **Расширенный редактор** содержит свойства, которые можно установить с помощью программных средств. Дополнительные сведения о свойствах, которые вы можете задать в диалоговом окне **Расширенный редактор** или программными средствами, см. в следующих разделах.  
  
-   [Общие свойства](../common-properties.md)  
  
-   [Пользовательские свойства назначения «Набор записей»](recordset-destination-custom-properties.md)  
  
 Дополнительные сведения о настройке свойств см. в разделе [Установление свойств компонента потока данных](set-the-properties-of-a-data-flow-component.md).  
  
## <a name="related-tasks"></a>Связанные задачи  
 [Использование назначения «Набор записей»](recordset-destination.md)  
  
  
