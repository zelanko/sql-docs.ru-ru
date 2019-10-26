---
title: Создание приложения поставщика SQL Server Native Client OLE DB | Документация Майкрософт
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, application creation
- applications [SQL Server Native Client]
- OLE DB, creating applications
ms.assetid: f3ae6815-f32d-4913-a1a2-2ba2f20cfd88
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 814758ebb1ff6554862372ef6cae03f94a38f7b9
ms.sourcegitcommit: 2a06c87aa195bc6743ebdc14b91eb71ab6b91298
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/25/2019
ms.locfileid: "72907128"
---
# <a name="creating-a-sql-server-native-client-ole-db-provider-application"></a>Создание приложения поставщика OLE DB для собственного клиента SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Создание приложения поставщика [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB включает следующие действия.  
  
1.  установление соединения с источником данных;  
  
2.  выполнение команды;  
  
3.  обработку результатов.  

> [!NOTE]  
>  По возможности используйте аутентификацию Windows. Если проверка подлинности Windows недоступна, запросите у пользователя ввод учетных данных во время выполнения. Избегайте хранения учетных данных в файле. Если необходимо сохранение учетных данных, зашифруйте их с помощью [API-интерфейса шифрования Win32](https://go.microsoft.com/fwlink/?LinkId=9504).  
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [Установка подключения к источнику данных](../../relational-databases/native-client-ole-db-provider/establishing-a-connection-to-a-data-source.md)  
  
-   [Выполнение команды](../../relational-databases/native-client-ole-db-provider/executing-a-command.md)  
  
-   [Обработка результатов](../../relational-databases/native-client-ole-db-provider/processing-results.md)  
  
-   [О свойствах OLE DB](../../relational-databases/native-client-ole-db-provider/about-ole-db-properties.md)  
  
-   [Использование предложения OUTPUT с OLE DB в SQL Server Native Client](../../relational-databases/native-client-ole-db-provider/using-the-output-clause-with-ole-db-in-sql-server-native-client.md)  
  
## <a name="see-also"></a>См. также статью  
 [SQL Server Native Client (OLE DB)](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
