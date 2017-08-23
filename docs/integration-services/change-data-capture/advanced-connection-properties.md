---
title: "Дополнительные свойства подключения | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4edfab68-7e68-45e8-a3f3-a0049ff7eb9e
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 856dce7d9b5c984407e7c03cee56013d22103fec
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="advanced-connection-properties"></a>Дополнительные свойства соединения
  В диалоговом окне **Дополнительные свойства соединения** можно добавить дополнительные параметры в строку подключения.  
  
 В качестве дополнительных можно использовать любые параметры соединения ODBC, поддерживаемые используемым экземпляром базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Параметры, указанные в диалоговом окне **Дополнительные свойства соединения** , добавляются к параметрам, выбранным в диалоговом окне **Соединение с SQL Server** .  
  
 Последний экземпляр каждого заданного параметра переопределяет все предыдущие экземпляры этого параметра. Параметры, добавленные в диалоговом окне **Дополнительные параметры соединения** , дополняют и заменяют параметры, заданные в диалоговом окне **Соединение с SQL Server** . Например, если в диалоговом окне **Соединение с SQL Server** в качестве имени сервера указано SERVER1, а диалоговое окно **Дополнительные параметры соединения** содержит строку ;SERVER=SERVER2, то соединение будет установлено с сервером SERVER2.  
  
 Параметры, добавляемые в диалоговом окне **Дополнительные свойства соединения** , передаются в виде обычного текста.  
  
> [!IMPORTANT]  
>  Не указывайте учетные данные для входа в диалоговом окне **Дополнительные свойства соединения** . Они не будут зашифрованы при передаче по сети.  
  
## <a name="see-also"></a>См. также  
 [Доступ к консоли конструктора CDC](../../integration-services/change-data-capture/access-the-cdc-designer-console.md)   
 [Соединение с SQL Server для создания экземпляров](../../integration-services/change-data-capture/sql-server-connection-for-instance-creation.md)  
  
  
