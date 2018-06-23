---
title: Удаление модуля обработки данных | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- deleting data processing extensions
- data processing extensions [Reporting Services], removing
- removing data processing extensions
ms.assetid: 1d89e32b-0631-44f6-8178-a57fb791d26d
caps.latest.revision: 33
author: douglaslM
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 0ea72edfcea9935b858631a639ec51f67a3feeac
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36190156"
---
# <a name="removing-a-data-processing-extension"></a>Удаление модуля обработки данных
  Чтобы удалить модуль обработки данных, просто удалите элемент **Extension** для модуля обработки данных в файле конфигурации. Если выполнены записи для сервера отчетов, а также для конструктора отчетов, удалите элемент **Extension** из файла RSReportServer.config и из файла RSReportDesigner.config. После удаления сведений о конфигурации модуль обработки данных становится недоступным компоненту.  
  
## <a name="see-also"></a>См. также  
 [Модули служб Reporting Services](../reporting-services-extensions.md)   
 [Реализация модуля обработки данных](implementing-a-data-processing-extension.md)   
 [Библиотека модулей Reporting Services](../reporting-services-extension-library.md)  
  
  