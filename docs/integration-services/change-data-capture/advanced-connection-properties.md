---
title: Дополнительные свойства соединения | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 4edfab68-7e68-45e8-a3f3-a0049ff7eb9e
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: ad7666ea6647d370d4f40b961cbd7e2aec643697
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47677882"
---
# <a name="advanced-connection-properties"></a>Дополнительные свойства соединения
  В диалоговом окне **Дополнительные свойства соединения** можно добавить дополнительные параметры в строку подключения.  
  
 В качестве дополнительных можно использовать любые параметры соединения ODBC, поддерживаемые используемым экземпляром базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Параметры, указанные в диалоговом окне **Дополнительные свойства соединения** , добавляются к параметрам, выбранным в диалоговом окне **Соединение с SQL Server** .  
  
 Последний экземпляр каждого заданного параметра переопределяет все предыдущие экземпляры этого параметра. Параметры, добавленные в диалоговом окне **Дополнительные параметры соединения** , дополняют и заменяют параметры, заданные в диалоговом окне **Соединение с SQL Server** . Например, если в диалоговом окне **Соединение с SQL Server** в качестве имени сервера указано SERVER1, а диалоговое окно **Дополнительные параметры соединения** содержит строку ;SERVER=SERVER2, то соединение будет установлено с сервером SERVER2.  
  
 Параметры, добавляемые в диалоговом окне **Дополнительные свойства соединения** , передаются в виде обычного текста.  
  
> [!IMPORTANT]  
>  Не указывайте учетные данные для входа в диалоговом окне **Дополнительные свойства соединения** . Они не будут зашифрованы при передаче по сети.  
  
## <a name="see-also"></a>См. также:  
 [Доступ к консоли конструктора CDC](../../integration-services/change-data-capture/access-the-cdc-designer-console.md)   
 [Соединение с SQL Server для создания экземпляров](../../integration-services/change-data-capture/sql-server-connection-for-instance-creation.md)  
  
  
