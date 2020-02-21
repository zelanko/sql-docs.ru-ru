---
title: Использование пользовательских сборок с отчетами | Документы Майкрософт
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: custom-assemblies
ms.topic: reference
helpviewer_keywords:
- custom assemblies [Reporting Services]
- assemblies [Reporting Services], custom
- custom assemblies [Reporting Services], about custom assemblies
ms.assetid: 53d141d0-2185-466a-84dc-7b90d284da3d
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 94fdcbb6219aefb0cf38f0d77c0c3437ccf19915
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "63194094"
---
# <a name="using-custom-assemblies-with-reports"></a>Использование пользовательских сборок с отчетами
  В службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] можно создавать пользовательский код для значений элементов отчета, стилей и форматирования. Так, пользовательский код можно использовать для форматирования валют в зависимости от настроек локали, для применения к определенным значениям специальных методов форматирования или для использования других бизнес-правил, установленных в конкретной компании. В частности, можно включить такой код в отчеты, создав пользовательскую сборку кода с помощью среды [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], на которую можно будет сослаться из файлов определения отчета. Сервер вызывает функции пользовательских сборок при выполнении отчета. Пользовательские сборки можно применять для получения значений специализированных функций, которые намечено использовать в отчетах.  
  
## <a name="in-this-section"></a>в этом разделе  
 [Ссылки на сборки в RDL-файле](../../reporting-services/custom-assemblies/referencing-assemblies-in-an-rdl-file.md)  
 Описывает способ создания ссылок на пользовательские сборки в файле языка определения отчета.  
  
 [Развертывание пользовательской сборки](../../reporting-services/custom-assemblies/deploying-a-custom-assembly.md)  
 Описывает способ развертывания пользовательских сборок в конструкторе отчетов и на сервере отчетов.  
  
 [Использование пользовательских сборок со строгими именами](../../reporting-services/custom-assemblies/using-strong-named-custom-assemblies.md)  
 Описывает способ применения пользовательских сборок со строгими именами.  
  
 [Проверка разрешений в пользовательских сборках](../../reporting-services/custom-assemblies/asserting-permissions-in-custom-assemblies.md)  
 Описывает способ развертывания пользовательских сборок с ограниченными и конкретными разрешениями, а также способ подтверждения этих разрешений в коде.  
  
 [Доступ к пользовательским сборкам с использованием выражений](../../reporting-services/custom-assemblies/accessing-custom-assemblies-through-expressions.md)  
 Описывает способ вызова методов пользовательских сборок в виде выражений отчетов в определениях отчетов.  
  
 [Инициализация объектов пользовательских сборок](../../reporting-services/custom-assemblies/initializing-custom-assembly-objects.md)  
 Описывает способ инициализации значений для объектов пользовательских сборок, вызываемых из отчета.  
  
 [Руководство. Отладка пользовательских сборок](../../reporting-services/custom-assemblies/how-to-debug-custom-assemblies.md)  
 Описывает способ отладки кода пользовательских сборок.  
  
## <a name="see-also"></a>См. также:  
 [Язык определения отчетов (службы SSRS)](../../reporting-services/reports/report-definition-language-ssrs.md)  
  
  
