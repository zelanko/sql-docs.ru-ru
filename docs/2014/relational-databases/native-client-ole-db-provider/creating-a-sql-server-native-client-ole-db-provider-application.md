---
title: Создание приложения поставщика SQL Server Native Client OLE DB | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, application creation
- applications [SQL Server Native Client]
- OLE DB, creating applications
ms.assetid: f3ae6815-f32d-4913-a1a2-2ba2f20cfd88
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 36416967a76631e59d5d122105b74be357e654de
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82704761"
---
# <a name="creating-a-sql-server-native-client-ole-db-provider-application"></a>Создание приложения поставщика OLE DB для собственного клиента SQL Server
  Создание [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] приложения поставщика собственного клиента OLE DB включает следующие шаги:  
  
1.  установление соединения с источником данных;  
  
2.  выполнение команды;  
  
3.  обработку результатов.  
  
> [!NOTE]  
>  По возможности используйте аутентификацию Windows. Если проверка подлинности Windows недоступна, запросите у пользователя ввод учетных данных во время выполнения. Избегайте хранения учетных данных в файле. Если необходимо сохранение учетных данных, зашифруйте их с помощью [API-интерфейса шифрования Win32](https://go.microsoft.com/fwlink/?LinkId=9504).  
  
## <a name="in-this-section"></a>В этом разделе  
  
-   [Установление соединения с источником данных](establishing-a-connection-to-a-data-source.md)  
  
-   [Исполнение команды](executing-a-command.md)  
  
-   [Обработка результатов](processing-results.md)  
  
-   [О свойствах OLE DB](about-ole-db-properties.md)  
  
-   [Использование предложения OUTPUT с OLE DB в SQL Server Native Client](using-the-output-clause-with-ole-db-in-sql-server-native-client.md)  
  
## <a name="see-also"></a>См. также  
 [SQL Server Native Client (OLE DB)](../native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
