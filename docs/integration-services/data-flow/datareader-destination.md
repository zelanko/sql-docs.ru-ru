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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 3cb33e3042ced47e0ac1e97377985b20299aa0af
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47595152"
---
# <a name="datareader-destination"></a>назначение DataReader
  Назначение DataReader извлекает данные из потока данных с помощью интерфейса ADO.NET **DataReader** . Эти данные могут быть впоследствии использованы другими приложениями. Например, можно настроить источник данных из отчета служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] на использование результата выполнения пакета служб [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Для этого нужно создать поток данных, который реализует назначение DataReader.  
  
 Дополнительные сведения о доступе и чтении значений в назначении DataReader программным способом см. в разделе [Загрузка выхода локального пакета](../../integration-services/run-manage-packages-programmatically/loading-the-output-of-a-local-package.md).  
  
## <a name="configuration-of-the-datareader-destination"></a>Настройка назначения «DataReader»  
 Можно указать значение времени ожидания для назначения DataReader и установить, должно ли назначение завершиться неудачей по истечении времени ожидания. Время ожидания истекает, если приложение не требует данных в течение заданного промежутка времени.  
  
 Назначение DataReader имеет один вход. Вывод ошибок не поддерживается.  
  
 Значения свойств можно задавать с помощью конструктора [!INCLUDE[ssIS](../../includes/ssis-md.md)] или программными средствами.  
  
 Дополнительные сведения о свойствах, которые вы можете задать в диалоговом окне **Расширенный редактор** или программными средствами, см. в следующих разделах.  
  
-   [Common Properties](http://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)  
  
-   [Пользовательские свойства назначения «Модуль чтения данных»](../../integration-services/data-flow/datareader-destination-custom-properties.md)  
  
 Дополнительные сведения о настройке свойств см. в разделе [Установление свойств компонента потока данных](../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md).  
  
  
