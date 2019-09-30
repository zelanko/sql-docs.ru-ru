---
title: Назначение DataReader | Документы Майкрософт
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.datareaderdest.f1
helpviewer_keywords:
- DataReader destination
- destinations [Integration Services], DataReader
ms.assetid: 56fcc4bf-c901-42c3-a71d-110039293431
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 484464550b08f209bb271a806c496e87417c0d99
ms.sourcegitcommit: e8af8cfc0bb51f62a4f0fa794c784f1aed006c71
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/26/2019
ms.locfileid: "71293067"
---
# <a name="datareader-destination"></a>назначение DataReader

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Назначение DataReader извлекает данные из потока данных с помощью интерфейса ADO.NET **DataReader** . Эти данные могут быть впоследствии использованы другими приложениями. Например, можно настроить источник данных из отчета служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] на использование результата выполнения пакета служб [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Для этого нужно создать поток данных, который реализует назначение DataReader.  
  
 Дополнительные сведения о доступе и чтении значений в назначении DataReader программным способом см. в разделе [Загрузка выхода локального пакета](../../integration-services/run-manage-packages-programmatically/loading-the-output-of-a-local-package.md).  
  
## <a name="configuration-of-the-datareader-destination"></a>Настройка назначения «DataReader»  
 Можно указать значение времени ожидания для назначения DataReader и установить, должно ли назначение завершиться неудачей по истечении времени ожидания. Время ожидания истекает, если приложение не требует данных в течение заданного промежутка времени.  
  
 Назначение DataReader имеет один вход. Вывод ошибок не поддерживается.  
  
 Значения свойств можно задавать с помощью конструктора [!INCLUDE[ssIS](../../includes/ssis-md.md)] или программными средствами.  
  
 Дополнительные сведения о свойствах, которые вы можете задать в диалоговом окне **Расширенный редактор** или программными средствами, см. в следующих разделах.  
  
-   [Общие свойства](https://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)  
  
-   [Пользовательские свойства назначения «Модуль чтения данных»](../../integration-services/data-flow/datareader-destination-custom-properties.md)  
  
 Дополнительные сведения о настройке свойств см. в разделе [Установление свойств компонента потока данных](../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md).  
  
  
