---
title: "Диспетчер подключений службы хранилища Azure | Документы Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.afpstorageconn.f1
- sql14.dts.designer.afpstorageconn.f1
ms.assetid: 68bd1d04-d20f-4357-a34e-7c9c76457062
caps.latest.revision: 13
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 848b0f0e3e639d31fa739e8d744fc4b80839a5fd
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="azure-storage-connection-manager"></a>Диспетчер подключений службы хранилища Azure
  **Диспетчер подключений службы хранилища Azure** позволяет использовать пакет SSIS для подключения к учетной записи хранения Azure с помощью указываемых значений свойств: имени учетной записи хранения и ключа учетной записи.  
   
 **Диспетчер подключений службы хранилища Azure** — это компонент [пакет дополнительных компонентов SQL Server Integration Services (SSIS) для Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md). 
  
1.  В диалоговом окне **Добавление диспетчера соединений со службами SSIS** выберите **AzureStorage**и щелкните **Добавить**.  
  
2.  В диалоговом окне редактора диспетчера подключений службы хранилища Azure выберите **Use Azure account** (Использовать учетную запись Azure), чтобы подключиться к службе хранилища Azure через Интернет, или выберите **Use local developer account** (Использовать локальную учетную запись разработчика), чтобы подключиться к локальной службе, размещенной эмулятором хранения Azure.  
  
3.  Если вы выбрали параметр **Use Azure account** (Использовать учетную запись Azure), выполните следующее.  
  
    1.  Укажите значения для полей **Имя учетной записи хранения** и **Ключ учетной записи** . Эти значения будут храниться как конфиденциальные данные в пакете SSIS.  
  
    2.  Выберите параметр **Использовать HTTPS** , если для подключения к службе хранилища Azure хотите использовать протокол HTTPS, а не HTTP.  
  
4.  Чтобы закрыть диалоговое окно, нажмите кнопку **ОК** .  
  
5.  Свойства созданного диспетчера соединений можно просмотреть в окне **Свойства** .  
  
  

