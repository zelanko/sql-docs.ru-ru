---
title: Использование пользовательских сборок с отчетами | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- custom assemblies [Reporting Services]
- assemblies [Reporting Services], custom
- custom assemblies [Reporting Services], about custom assemblies
ms.assetid: 53d141d0-2185-466a-84dc-7b90d284da3d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e79f48f4e4a2eb5fbc83c353461709658caf2509
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63265655"
---
# <a name="using-custom-assemblies-with-reports"></a>Использование пользовательских сборок с отчетами
  В службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] можно создавать пользовательский код для значений элементов отчета, стилей и форматирования. Так, пользовательский код можно использовать для форматирования валют в зависимости от настроек локали, для применения к определенным значениям специальных методов форматирования или для использования других бизнес-правил, установленных в конкретной компании. В частности, можно включить такой код в отчеты, создав пользовательскую сборку кода с помощью среды [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], на которую можно будет сослаться из файлов определения отчета. Сервер вызывает функции пользовательских сборок при выполнении отчета. Пользовательские сборки можно применять для получения значений специализированных функций, которые намечено использовать в отчетах.  
  
## <a name="in-this-section"></a>в этом разделе  
 [Ссылки на сборки в RDL-файле](referencing-assemblies-in-an-rdl-file.md)  
 Описывает способ создания ссылок на пользовательские сборки в файле языка определения отчета.  
  
 [Развертывание пользовательской сборки](deploying-a-custom-assembly.md)  
 Описывает способ развертывания пользовательских сборок в конструкторе отчетов и на сервере отчетов.  
  
 [Использование пользовательских сборок со строгими именами](using-strong-named-custom-assemblies.md)  
 Описывает способ применения пользовательских сборок со строгими именами.  
  
 [Проверка разрешений в пользовательских сборках](asserting-permissions-in-custom-assemblies.md)  
 Описывает способ развертывания пользовательских сборок с ограниченными и конкретными разрешениями, а также способ подтверждения этих разрешений в коде.  
  
 [Доступ к пользовательским сборкам с использованием выражений](accessing-custom-assemblies-through-expressions.md)  
 Описывает способ вызова методов пользовательских сборок в виде выражений отчетов в определениях отчетов.  
  
 [Инициализация объектов пользовательских сборок](initializing-custom-assembly-objects.md)  
 Описывает способ инициализации значений для объектов пользовательских сборок, вызываемых из отчета.  
  
 [Как Отладка пользовательских сборок](how-to-debug-custom-assemblies.md)  
 Описывает способ отладки кода пользовательских сборок.  
  
## <a name="see-also"></a>См. также  
 [Язык определения отчетов (службы SSRS)](../reports/report-definition-language-ssrs.md)  
  
  
