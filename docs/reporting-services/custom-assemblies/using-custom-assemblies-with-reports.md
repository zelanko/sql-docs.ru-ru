---
title: "Использование пользовательских сборок с отчетами | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
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
- custom assemblies [Reporting Services]
- assemblies [Reporting Services], custom
- custom assemblies [Reporting Services], about custom assemblies
ms.assetid: 53d141d0-2185-466a-84dc-7b90d284da3d
caps.latest.revision: 32
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: fb818ce570a542a3cfcccec5c9290821c4e21181
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="using-custom-assemblies-with-reports"></a>Использование пользовательских сборок с отчетами
  В службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] можно создавать пользовательский код для значений элементов отчета, стилей и форматирования. Так, пользовательский код можно использовать для форматирования валют в зависимости от настроек локали, для применения к определенным значениям специальных методов форматирования или для использования других бизнес-правил, установленных в конкретной компании. Для включения этого кода в отчетах можно создать сборку пользовательского кода с помощью [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] , в можно ссылаться из файлов определения отчета. Сервер вызывает функции пользовательских сборок при выполнении отчета. Пользовательские сборки можно применять для получения значений специализированных функций, которые намечено использовать в отчетах.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Ссылки на сборки в RDL-файл](../../reporting-services/custom-assemblies/referencing-assemblies-in-an-rdl-file.md)  
 Описывает способ создания ссылок на пользовательские сборки в файле языка определения отчета.  
  
 [Развертывание пользовательской сборки](../../reporting-services/custom-assemblies/deploying-a-custom-assembly.md)  
 Описывает способ развертывания пользовательских сборок в конструкторе отчетов и на сервере отчетов.  
  
 [Использование пользовательских сборок со строгими именами](../../reporting-services/custom-assemblies/using-strong-named-custom-assemblies.md)  
 Описывает способ применения пользовательских сборок со строгими именами.  
  
 [Подтверждение разрешений в пользовательских сборках](../../reporting-services/custom-assemblies/asserting-permissions-in-custom-assemblies.md)  
 Описывает способ развертывания пользовательских сборок с ограниченными и конкретными разрешениями, а также способ подтверждения этих разрешений в коде.  
  
 [Доступ к пользовательским сборкам посредством выражений](../../reporting-services/custom-assemblies/accessing-custom-assemblies-through-expressions.md)  
 Описывает способ вызова методов пользовательских сборок в виде выражений отчетов в определениях отчетов.  
  
 [Инициализация объектов пользовательских сборок](../../reporting-services/custom-assemblies/initializing-custom-assembly-objects.md)  
 Описывает способ инициализации значений для объектов пользовательских сборок, вызываемых из отчета.  
  
 [Как: отладка пользовательских сборок](../../reporting-services/custom-assemblies/how-to-debug-custom-assemblies.md)  
 Описывает способ отладки кода пользовательских сборок.  
  
## <a name="see-also"></a>См. также:  
 [Язык определения отчетов &#40; Службы SSRS &#41;](../../reporting-services/reports/report-definition-language-ssrs.md)  
  
  
