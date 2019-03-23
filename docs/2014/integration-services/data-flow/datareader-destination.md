---
title: Назначение DataReader | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.datareaderdest.f1
helpviewer_keywords:
- DataReader destination
- destinations [Integration Services], DataReader
ms.assetid: 56fcc4bf-c901-42c3-a71d-110039293431
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 694e85a56686379d089f3c2fc11721e4dd6f8642
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2019
ms.locfileid: "58385932"
---
# <a name="datareader-destination"></a>назначение DataReader
  Назначение DataReader извлекает данные из потока данных с помощью интерфейса ADO.NET `DataReader`. Эти данные могут быть впоследствии использованы другими приложениями. Например, можно настроить источник данных из отчета служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] на использование результата выполнения пакета служб [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Для этого нужно создать поток данных, который реализует назначение DataReader.  
  
 Дополнительные сведения о доступе и чтении значений в назначении DataReader программным способом см. в разделе [Загрузка выхода локального пакета](../run-manage-packages-programmatically/loading-the-output-of-a-local-package.md).  
  
## <a name="configuration-of-the-datareader-destination"></a>Настройка назначения «DataReader»  
 Можно указать значение времени ожидания для назначения DataReader и установить, должно ли назначение завершиться неудачей по истечении времени ожидания. Время ожидания истекает, если приложение не требует данных в течение заданного промежутка времени.  
  
 Назначение DataReader имеет один вход. Вывод ошибок не поддерживается.  
  
 Значения свойств можно задавать с помощью конструктора [!INCLUDE[ssIS](../../includes/ssis-md.md)] или программными средствами.  
  
 Дополнительные сведения о свойствах, которые вы можете задать в диалоговом окне **Расширенный редактор** или программными средствами, см. в следующих разделах.  
  
-   [Общие свойства](../common-properties.md)  
  
-   [Пользовательские свойства назначения «Модуль чтения данных»](datareader-destination-custom-properties.md)  
  
 Дополнительные сведения о настройке свойств см. в разделе [Установление свойств компонента потока данных](set-the-properties-of-a-data-flow-component.md).  
  
  
