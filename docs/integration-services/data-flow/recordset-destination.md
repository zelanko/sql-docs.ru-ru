---
title: Назначение "Набора записей" | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.recordsetdest.f1
helpviewer_keywords:
- Recordset destination
- ADO recordsets [Integration Services]
- destinations [Integration Services], Recordset
- in-memory ADO recordsets [Integration Services]
ms.assetid: be973cf1-c4ff-49f8-987e-314c08ef98e4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fc14bf340407903674014a84a6b48f2ff14522fc
ms.sourcegitcommit: e8af8cfc0bb51f62a4f0fa794c784f1aed006c71
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/26/2019
ms.locfileid: "71298131"
---
# <a name="recordset-destination"></a>назначение «Набор записей»

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Назначение «Набора записей» создает и заполняет набор записей ADO в памяти. Форма набора записей определяется входными данными назначения «набор записей» во время проектирования.  
  
## <a name="configuration-of-the-recordset-destination"></a>Настройка назначения «Набор записей»  
 Назначение «Набор записей» настраивается с помощью указания переменной для хранения набора записей ADO.  
  
 Во время выполнения набор записей ADO записывается в переменную типа Object, заданную в свойстве VariableName назначения "Набор записей". Переменная делает набор записей доступным за пределами потока данных, где он может быть использован скриптами и другими элементами пакета.  
  
 У данного источника один вход. Вывод ошибок не поддерживается.  
  
 Значения свойств можно задавать с помощью конструктора [!INCLUDE[ssIS](../../includes/ssis-md.md)] или программными средствами.  
  
 Диалоговое окно **Расширенный редактор** содержит свойства, которые можно установить с помощью программных средств. Дополнительные сведения о свойствах, которые вы можете задать в диалоговом окне **Расширенный редактор** или программными средствами, см. в следующих разделах.  
  
-   [Общие свойства](https://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)  
  
-   [Пользовательские свойства назначения «Набор записей»](../../integration-services/data-flow/recordset-destination-custom-properties.md)  
  
 Дополнительные сведения о настройке свойств см. в разделе [Установление свойств компонента потока данных](../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md).  
  
## <a name="related-tasks"></a>Связанные задачи  
 [использовать назначение «Набор записей»](../../integration-services/data-flow/use-a-recordset-destination.md)  
  
  
