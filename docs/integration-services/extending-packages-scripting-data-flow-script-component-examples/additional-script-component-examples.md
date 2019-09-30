---
title: Дополнительные примеры компонента скрипта | Документы Майкрософт
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Script component [Integration Services], examples
ms.assetid: 849dd38a-abb5-4702-a413-882aae3980a5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d74a4a6ab596f6762e405a81b2365281b4f6b95c
ms.sourcegitcommit: e8af8cfc0bb51f62a4f0fa794c784f1aed006c71
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/26/2019
ms.locfileid: "71297103"
---
# <a name="additional-script-component-examples"></a>Дополнительные примеры компонента скрипта

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Компонент скрипта является настраиваемым средством, которое можно использовать в потоке данных пакета, чтобы выполнить практическое любое требование, которое не удается выполнить с помощью источников, преобразований и назначений, входящих в состав служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. В этом разделе содержатся образцы кода компонента скрипта, демонстрирующие различные типы доступной функциональности.  
  
 Примеры, демонстрирующие настройку компонента скрипта как источника, преобразования или назначения, см. в разделе [Разработка компонентов скрипта определенных типов](../../integration-services/extending-packages-scripting-data-flow-script-component-types/developing-specific-types-of-script-components.md).  
  
> [!NOTE]  
>  Если нужно создать компоненты, которые легко использовать повторно в нескольких задачах потока данных и нескольких пакетах, следует использовать код в приведенных образцах компонента скрипта в качестве начальной точки при создании компонентов пользовательского потока данных. Дополнительные сведения см. в разделе [Разработка пользовательского компонента потока данных](../../integration-services/extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md).  
  
## <a name="in-this-section"></a>в этом разделе  
 [Имитация вывода ошибок для компонента скрипта](../../integration-services/extending-packages-scripting-data-flow-script-component-examples/simulating-an-error-output-for-the-script-component.md)  
 Компонент скрипта не поддерживает стандартный вывод ошибок, но его можно эмулировать с помощью небольшой дополнительной настройки и написания простого кода.  
  
 [Расширение вывода ошибок с помощью компонента скрипта](../../integration-services/extending-packages-scripting-data-flow-script-component-examples/enhancing-an-error-output-with-the-script-component.md)  
 Объясняет и демонстрирует добавление дополнительных сведений к стандартному выводу ошибок с помощью компонента скрипта.  
  
 [Создание назначения ODBC с помощью компонента скрипта](../../integration-services/extending-packages-scripting-data-flow-script-component-examples/creating-an-odbc-destination-with-the-script-component.md)  
 Объясняет и демонстрирует создание назначения потока данных ODBC с помощью компонента скрипта.  
  
 [Синтаксический анализ текстовых файлов нестандартного формата в компоненте скрипта](../../integration-services/extending-packages-scripting-data-flow-script-component-examples/parsing-non-standard-text-file-formats-with-the-script-component.md)  
 Объясняет и демонстрирует анализ двух разных нестандартных текстовых форматов в целевые таблицы.  
  
  
