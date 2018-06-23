---
title: Диспетчер подключений службы хранилища Azure | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.afpstorageconn.f1
- sql11.dts.designer.afpstorageconn.f1
ms.assetid: 68bd1d04-d20f-4357-a34e-7c9c76457062
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 41ddc29a865b84ef01721931b0702476fe6b9ec1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36194535"
---
# <a name="azure-storage-connection-manager"></a>Диспетчер подключений службы хранилища Azure
  Диспетчер подключений службы хранилища Azure позволяет пакету служб SSIS для подключения к учетной записи хранилища Azure с помощью указываемых значений свойств: имени учетной записи хранения и ключ учетной записи.  
  
1.  В диалоговом окне **Добавление диспетчера соединений со службами SSIS** выберите **AzureStorage**и щелкните **Добавить**.  
  
2.  В диалоговом окне редактора диспетчера подключений службы хранилища Azure выберите **Use Azure account** (Использовать учетную запись Azure), чтобы подключиться к службе хранилища Azure через Интернет, или выберите **Use local developer account** (Использовать локальную учетную запись разработчика), чтобы подключиться к локальной службе, размещенной эмулятором хранения Azure.  
  
3.  Если вы выбрали параметр **Use Azure account** (Использовать учетную запись Azure), выполните следующее.  
  
    1.  Укажите значения для полей **Имя учетной записи хранения** и **Ключ учетной записи** . Эти значения будут храниться как конфиденциальные данные в пакете SSIS.  
  
    2.  Выберите параметр **Использовать HTTPS** , если для подключения к службе хранилища Azure хотите использовать протокол HTTPS, а не HTTP.  
  
4.  Чтобы закрыть диалоговое окно, нажмите кнопку **ОК** .  
  
5.  Свойства созданного диспетчера соединений можно просмотреть в окне **Свойства** .  
  
  