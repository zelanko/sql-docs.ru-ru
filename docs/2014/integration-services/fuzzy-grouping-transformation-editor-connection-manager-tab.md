---
title: Редактор преобразования Нечеткое группирование (вкладка «Диспетчер соединений») | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.fuzzygroupingtransformation.connection.f1
helpviewer_keywords:
- Fuzzy Grouping Transformation Editor
ms.assetid: 47b1446d-5331-473c-9cb5-a98b1f55bf5f
caps.latest.revision: 27
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 05c4af52fa196fe0c779ab3cef3be67d769b9616
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37164815"
---
# <a name="fuzzy-grouping-transformation-editor-connection-manager-tab"></a>Редактор преобразования «Нечеткое группирование» (вкладка «Диспетчер соединений»)
  Вкладка **Диспетчер соединений** в диалоговом окне **Редактор преобразования «Нечеткое группирование»** используется для выбора существующего соединения или для создания нового.  
  
> [!NOTE]  
>  Сервер, указанный в соединении, должен работать под управлением [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Преобразование "Нечеткое группирование" создает временные объекты в базе данных tempdb, размер которой может соответствовать полному вводу для преобразования. При выполнении преобразования запросы сервера выполняются в зависимости от этих временных объектов. Это может повлиять на общую производительность сервера.  
  
 Дополнительные сведения о преобразовании «Нечеткое группирование» см. в разделе [Fuzzy Grouping Transformation](data-flow/transformations/fuzzy-grouping-transformation.md).  
  
## <a name="options"></a>Параметры  
 **Диспетчер соединений OLE DB**  
 Выберите в списке существующий диспетчер соединения OLE DB или создайте новое соединение с помощью кнопки **Создать** .  
  
 **Создать**  
 Создайте новое соединение с помощью диалогового окна **Настройка диспетчера соединений OLE DB** .  
  
## <a name="see-also"></a>См. также  
 [Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Определение подобных строк данных с помощью преобразования "Нечеткое группирование"](data-flow/transformations/identify-similar-data-rows-by-using-the-fuzzy-grouping-transformation.md)  
  
  
