---
title: Архитектура пользовательских элементов отчета | Документы Майкрософт
description: Узнайте, что архитектура пользовательского элемента отчета является расширением, позволяющим разработчикам добавлять функции, которые изначально не поддерживаются в RDL.
ms.date: 03/03/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: custom-report-items
ms.topic: reference
helpviewer_keywords:
- custom report items, architecture
ms.assetid: 2a88ea46-c9f8-4dd7-aad1-16de11da4f06
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 039afae1b8be540869930055e77320c27857e23d
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "80216963"
---
# <a name="custom-report-item-architecture"></a>Архитектура пользовательских элементов отчета
  Пользовательский элемент отчета является расширением языка определения отчетов (RDL), позволяющим разработчикам добавлять функции, изначально не поддерживаемые в RDL, или расширять функциональные возможности существующих элементов управления. Существует два основных компонента пользовательского элемента отчета: компонент времени выполнения и компонент времени разработки. Эти компоненты реализованы как сборки платформы [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] и могут быть записаны на любом соответствующем CLS языке.  
  
## <a name="the-run-time-component"></a>Компонент времени выполнения  
 Компонент времени выполнения для пользовательского элемента отчета вызывается обработчиком отчетов во время выполнения. Компонент времени выполнения принимает данные, переданные обработчиком отчетов во время выполнения, обрабатывает эти данные и возвращает изображение, содержащее отображаемый пользовательский элемент отчета.  
  
 ![Пользовательский элемент отчета (компонент времени выполнения)](../../reporting-services/custom-report-items/media/customreportitemrun-timecomponentarchitecture.gif "Пользовательский элемент отчета (компонент времени выполнения)")  
  
## <a name="the-design-time-component"></a>Компонент времени разработки  
 Компонент времени разработки позволяет определять пользовательский элемент отчета и управлять этим элементом в интерфейсе конструктора отчетов в [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Компонент времени разработки состоит из нескольких вложенных элементов управления, которые контролируют внешний вид и свойства пользовательского элемента отчета в среде проектирования.  
  
 ![Пользовательский элемент отчета (компонент времени разработки)](../../reporting-services/custom-report-items/media/customreportitemdesign-timecomponentarchitecture.gif "Пользовательский элемент отчета (компонент времени разработки)")  
  
## <a name="see-also"></a>См. также:  
 [Создание компонента времени выполнения пользовательского элемента отчета](../../reporting-services/custom-report-items/creating-a-custom-report-item-run-time-component.md)   
 [Создание компонента времени разработки пользовательского элемента отчета](../../reporting-services/custom-report-items/creating-a-custom-report-item-design-time-component.md)   
 [Руководство. развернуть пользовательский элемент отчета](../../reporting-services/custom-report-items/how-to-deploy-a-custom-report-item.md)  
  
  
