---
title: "Регулярные vs. Контекстные соединения | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: clr
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- context connections [CLR integration]
- regular connections [CLR integration]
ms.assetid: a1dead02-be88-4b16-8cb2-db1284856764
caps.latest.revision: "13"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6b15a8e2c830c0f8e367aa9b2efc60a6911ee25e
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="context-connections-vs-regular-connections"></a>Vs контекст соединения. Обычные соединения
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]При подключении к удаленному серверу, всегда используйте стандартные соединения, а не контекстными соединениями. Если нужно подключиться к тому же серверу, на котором выполняется хранимая процедура или функция, в большинстве случаев используется контекстное соединение. Преимущества заключаются в выполнении приложений в одной области транзакций и отсутствии необходимости повторной проверки подлинности имени входа.  
  
 Кроме того, использование контекстного соединения обычно приводит к повышению производительности при меньшем потреблении ресурсов. Контекстное соединение является только внутрипроцессным соединением, поэтому оно может связываться с сервером «напрямую», обходя сетевой протокол и транспортный уровень при отправке инструкций Transact-SQL и получении результатов. Также обходится процесс проверки подлинности. На следующем рисунке показана основные компоненты **SqlClient** управляемого поставщика, а также как различные компоненты взаимодействуют друг с другом, при использовании обычного и контекстного соединения.  
  
 ![Кодовые пути контекстного и обычного соединений. ] (../../../relational-databases/clr-integration/data-access/media/clrintdataaccess.gif "Кодовые пути контекстного и обычного соединений.")  
  
 Контекстное соединение требует более короткого кода и меньшего числа компонентов, поэтому запрос к серверу, как и получение результатов, происходит быстрее, чем при обычном соединении. Время выполнение запроса на сервере остается одинаковым для контекстных и обычных соединений.  
  
 В некоторых случаях, возможно, потребуется открыть отдельное обычное соединение с тем же сервером. Например, существуют некоторые ограничения на использование контекстных соединений, описанные в [ограничения обычных и контекстных соединений](../../../relational-databases/clr-integration/data-access/context-connections-and-regular-connections-restrictions.md).  
  
## <a name="see-also"></a>См. также:  
 [Контекстное соединение](../../../relational-databases/clr-integration/data-access/context-connection.md)  
  
  
