---
title: Архитектура пользовательских элементов отчета | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.topic: reference
helpviewer_keywords:
- custom report items, architecture
ms.assetid: 2a88ea46-c9f8-4dd7-aad1-16de11da4f06
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 3d75fed63f44e0371b81fbd7309a0a3f826543b5
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/27/2018
ms.locfileid: "52401057"
---
# <a name="custom-report-item-architecture"></a>Архитектура пользовательских элементов отчета
  Пользовательский элемент отчета является расширением языка определения отчетов (RDL), позволяющим разработчикам добавлять функции, изначально не поддерживаемые в RDL, или расширять функциональные возможности существующих элементов управления. Существует два основных компонента пользовательского элемента отчета: компонент времени выполнения и компонент времени разработки. Эти компоненты реализованы как сборки платформы [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] и могут быть записаны на любом соответствующем CLS языке.  
  
## <a name="the-run-time-component"></a>Компонент времени выполнения  
 Компонент времени выполнения для пользовательского элемента отчета вызывается обработчиком отчетов во время выполнения. Компонент времени выполнения принимает данные, переданные обработчиком отчетов во время выполнения, обрабатывает эти данные и возвращает изображение, содержащее отображаемый пользовательский элемент отчета.  
  
 ![Пользовательский элемент отчета (компонент времени выполнения)](../../../2014/reporting-services/media/customreportitemrun-timecomponentarchitecture.gif "Пользовательский элемент отчета (компонент времени выполнения)")  
  
## <a name="the-design-time-component"></a>Компонент времени разработки  
 Компонент времени разработки позволяет определять пользовательский элемент отчета и управлять этим элементом в интерфейсе конструктора отчетов в [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Компонент времени разработки состоит из нескольких вложенных элементов управления, которые контролируют внешний вид и свойства пользовательского элемента отчета в среде проектирования.  
  
 ![Пользовательский элемент отчета (компонент времени разработки)](../../../2014/reporting-services/media/customreportitemdesign-timecomponentarchitecture.gif "Пользовательский элемент отчета (компонент времени разработки)")  
  
## <a name="see-also"></a>См. также:  
 [Создание компонента времени выполнения пользовательского элемента отчета](../custom-report-items/creating-a-custom-report-item-run-time-component.md)   
 [Создание компонента времени разработки пользовательского элемента отчета](../custom-report-items/creating-a-custom-report-item-design-time-component.md)   
 [Как Развертывание пользовательского элемента отчета](../custom-report-items/how-to-deploy-a-custom-report-item.md)  
  
  
