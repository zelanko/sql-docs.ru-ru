---
title: Редактор преобразования Нечеткое группирование (вкладка «Диспетчер соединений») | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.fuzzygroupingtransformation.connection.f1
helpviewer_keywords:
- Fuzzy Grouping Transformation Editor
ms.assetid: 47b1446d-5331-473c-9cb5-a98b1f55bf5f
caps.latest.revision: 27
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: b3327aa60445bf3cb75d43d04652566cb886e331
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36097306"
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
 [Об ошибках служб Integration Services и справочник по сообщениям](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Определение подобных строк данных с помощью преобразования "Нечеткое группирование"](data-flow/transformations/identify-similar-data-rows-by-using-the-fuzzy-grouping-transformation.md)  
  
  