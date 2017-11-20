---
title: "Средство просмотра данных | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: data-flow
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.dataviewer.f1
helpviewer_keywords:
- Data Viewer dialog box
ms.assetid: 6351309a-688f-4e82-9697-1712130f10a1
caps.latest.revision: 13
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: a04115502f54ce1731c0d8aa14b2f264bc66709f
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="data-viewer"></a>Средство просмотра данных
  Если настроен путь для применения средства просмотра данных, то это средство отображает данные буфер за буфером по мере перемещения данных между двумя компонентами потока данных.  
  
## <a name="options"></a>Параметры  
 **Зеленая стрелка**  
 Переход к данным в следующем буфере. Если данные можно переместить в одиночный буфер, то этот параметр недоступен.  
  
 **Отсоединить**  
 Отсоединить средство просмотра данных.  
  
 **Примечание.** Отсоединение средства просмотра данных не приводит к удалению самого средства. При отсоединении средства просмотра данных данные продолжают следовать по пути, однако данные в средстве просмотра не обновляются для поддержания соответствия с данными в каждом буфере.  
  
 **Присоединить**  
 Присоединить средство просмотра данных.  
  
 **Примечание.** Когда средство просмотра данных присоединяется, оно отображает информация из каждого буфера потока данных, а затем приостанавливает свою работу. Можно перемещаться от буфера к буферу с помощью зеленой стрелки.  
  
 **Скопировать данные**  
 Копирование данных текущего буфера в буфер обмена.  
  
## <a name="see-also"></a>См. также  
 [Отладка потока данных](../../integration-services/troubleshooting/debugging-data-flow.md)  
  
  

