---
title: "Архитектура пользовательского элемента отчета | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- custom report items, architecture
ms.assetid: 2a88ea46-c9f8-4dd7-aad1-16de11da4f06
caps.latest.revision: 16
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 8b79071c67e3ada6fcfc0f588d9cba4580a981e8
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="custom-report-item-architecture"></a>Архитектура пользовательских элементов отчета
  Пользовательский элемент отчета является расширением языка определения отчетов (RDL), позволяющим разработчикам добавлять функции, изначально не поддерживаемые в RDL, или расширять функциональные возможности существующих элементов управления. Существует два основных компонента пользовательского элемента отчета: компонент времени выполнения и компонент времени разработки. Эти компоненты реализованы как сборки платформы [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] и могут быть записаны на любом CLS-совместимом языке.  
  
## <a name="the-run-time-component"></a>Компонент времени выполнения  
 Компонент времени выполнения для пользовательского элемента отчета вызывается обработчиком отчетов во время выполнения. Компонент времени выполнения принимает данные, переданные обработчиком отчетов во время выполнения, обрабатывает эти данные и возвращает изображение, содержащее отображаемый пользовательский элемент отчета.  
  
 ![Компонента пользовательского элемента отчета времени выполнения](../../reporting-services/custom-report-items/media/customreportitemrun-timecomponentarchitecture.gif "компонента во время выполнения элемента пользовательского отчета")  
  
## <a name="the-design-time-component"></a>Компонент времени разработки  
 Компонент времени разработки позволяет определять пользовательский элемент отчета и управлять этим элементом в интерфейсе конструктора отчетов в [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Компонент времени разработки состоит из нескольких вложенных элементов управления, которые контролируют внешний вид и свойства пользовательского элемента отчета в среде проектирования.  
  
 ![Компонента пользовательского элемента отчета времени разработки](../../reporting-services/custom-report-items/media/customreportitemdesign-timecomponentarchitecture.gif "компонента времени разработки элемента пользовательского отчета")  
  
## <a name="see-also"></a>См. также:  
 [Создание компонента пользовательского элемента отчета времени выполнения](../../reporting-services/custom-report-items/creating-a-custom-report-item-run-time-component.md)   
 [Создание компонента пользовательского элемента отчета времени разработки](../../reporting-services/custom-report-items/creating-a-custom-report-item-design-time-component.md)   
 [Как: развертывание пользовательского элемента отчета](../../reporting-services/custom-report-items/how-to-deploy-a-custom-report-item.md)  
  
  
