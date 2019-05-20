---
title: Диспетчер подключений службы хранилища Azure | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.afpstorageconn.f1
- sql14.dts.designer.afpstorageconn.f1
ms.assetid: 68bd1d04-d20f-4357-a34e-7c9c76457062
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 509e51243f7de4e6871bedf18c7ce7aa84d3e8c6
ms.sourcegitcommit: fd71d04a9d30a9927cbfff645750ac9d5d5e5ee7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/16/2019
ms.locfileid: "65728330"
---
# <a name="azure-storage-connection-manager"></a>Диспетчер подключений службы хранилища Azure

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  **Диспетчер подключений службы хранилища Azure** позволяет пакету служб SSIS подключаться к подписке Azure с помощью указываемых вами значений свойств: имени учетной записи хранения и ключа учетной записи.  
   
 **Диспетчер подключений службы хранилища Azure** входит в состав пакета дополнительных компонентов [SQL Server Integration Services (SSIS) для Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md). 
  
1.  В диалоговом окне **Добавление диспетчера соединений со службами SSIS** выберите **AzureStorage**и щелкните **Добавить**.  
  
2.  В диалоговом окне редактора диспетчера подключений службы хранилища Azure выберите **Use Azure account** (Использовать учетную запись Azure), чтобы подключиться к службе хранилища Azure через Интернет, или выберите **Use local developer account** (Использовать локальную учетную запись разработчика), чтобы подключиться к локальной службе, размещенной эмулятором хранения Azure.  
  
3.  Если вы выбрали параметр **Use Azure account** (Использовать учетную запись Azure), выполните следующее.  
  
    1.  Укажите значения для полей **Имя учетной записи хранения** и **Ключ учетной записи** . Эти значения будут храниться как конфиденциальные данные в пакете SSIS.  
  
    2.  Выберите параметр **Использовать HTTPS** , если для подключения к службе хранилища Azure хотите использовать протокол HTTPS, а не HTTP.  
  
4.  Чтобы закрыть диалоговое окно, нажмите кнопку **ОК** .  
  
5.  Свойства созданного диспетчера соединений можно просмотреть в окне **Свойства** .  
  
  
