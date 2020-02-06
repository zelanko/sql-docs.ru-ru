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
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 70e8c3cbc08837bce7c3b8aa9afeb3222165996c
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "71298917"
---
# <a name="advanced-connection-properties"></a>Дополнительные свойства соединения

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


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
  
  
