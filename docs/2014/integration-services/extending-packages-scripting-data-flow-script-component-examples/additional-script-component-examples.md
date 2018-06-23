---
title: Дополнительные примеры компонента скрипта | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- integration-services
ms.tgt_pltfrm: ''
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Script component [Integration Services], examples
ms.assetid: 849dd38a-abb5-4702-a413-882aae3980a5
caps.latest.revision: 29
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 2fd90743bcae3675e4ca1ffa455873fa79bef211
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36188286"
---
# <a name="additional-script-component-examples"></a>Дополнительные примеры компонента скрипта
  Компонент скрипта является настраиваемым средством, которое можно использовать в потоке данных пакета, чтобы выполнить практическое любое требование, которое не удается выполнить с помощью источников, преобразований и назначений, входящих в состав служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. В этом разделе содержатся образцы кода компонента скрипта, демонстрирующие различные типы доступной функциональности.  
  
 Примеры, демонстрирующие настройку компонента скрипта как источника, преобразования или назначения, см. в разделе [Разработка компонентов скрипта определенных типов](../extending-packages-scripting-data-flow-script-component-types/developing-specific-types-of-script-components.md).  
  
> [!NOTE]  
>  Если нужно создать компоненты, которые легко использовать повторно в нескольких задачах потока данных и нескольких пакетах, следует использовать код в приведенных образцах компонента скрипта в качестве начальной точки при создании компонентов пользовательского потока данных. Дополнительные сведения см. в разделе [Разработка пользовательского компонента потока данных](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md).  
  
## <a name="in-this-section"></a>в этом разделе  
 [Имитация вывода ошибок для компонента скрипта](../extending-packages-scripting-data-flow-script-component-examples/simulating-an-error-output-for-the-script-component.md)  
 Компонент скрипта не поддерживает стандартный вывод ошибок, но его можно эмулировать с помощью небольшой дополнительной настройки и написания простого кода.  
  
 [Расширение вывода ошибок с помощью компонента скрипта](../extending-packages-scripting-data-flow-script-component-examples/enhancing-an-error-output-with-the-script-component.md)  
 Объясняет и демонстрирует добавление дополнительных сведений к стандартному выводу ошибок с помощью компонента скрипта.  
  
 [Создание назначения ODBC с помощью компонента скрипта](../extending-packages-scripting-data-flow-script-component-examples/creating-an-odbc-destination-with-the-script-component.md)  
 Объясняет и демонстрирует создание назначения потока данных ODBC с помощью компонента скрипта.  
  
 [Синтаксический анализ текстовых файлов нестандартного формата в компоненте скрипта](../extending-packages-scripting-data-flow-script-component-examples/parsing-non-standard-text-file-formats-with-the-script-component.md)  
 Объясняет и демонстрирует анализ двух разных нестандартных текстовых форматов в целевые таблицы.  
  
![Значок служб Integration Services (маленький)](../media/dts-16.gif "значок служб Integration Services (маленький)")**оставаться установка последних со службами Integration Services** <br /> Чтобы загрузить новейшую документацию, статьи, образцы и видеоматериалы корпорации Майкрософт, а также лучшие решения участников сообщества, посетите страницу служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] на сайте MSDN:<br /><br /> [Посетите страницу служб Integration Services в MSDN](http://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Чтобы получать автоматические уведомления об этих обновлениях, подпишитесь на RSS-каналы, предлагаемые на этой странице.  
  
  