---
title: Подключение к Windows Azure хранилища (восстановление) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: backup-restore
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.restore.connectstorage.f1
ms.assetid: c0b7d7c8-b878-4b7f-8120-d0c6917b583f
caps.latest.revision: 5
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 63f7f0e06a94d9d6a05995e9c19f24f0b8d46047
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37172905"
---
# <a name="connect-to-windows-azure-storage-restore"></a>Соединение с хранилищем Windows Azure (восстановление)
  Это диалоговое окно позволяет указать сведения для подключения к учетной записи хранения Windows Azure для получения файлов в учетной записи хранения. После ввода необходимой информации нажмите кнопку **Подключить** , чтобы установить соединение с хранилищем Windows Azure.  
  
## <a name="windows-azure-storage-account"></a>Учетная запись хранения Windows Azure  
 **Учетная запись хранения**  
 Выберите, введите или вставьте имя учетной записи хранения Windows Azure. В раскрывающемся списке указаны ранее используемые учетные записи.  
  
 **Ключ учетной записи**  
 Укажите ключ доступа к учетной записи хранения Windows Azure.  
  
 Флажок**Использовать защищенные конечные точки (HTTPS)**   
 Установите этот флажок, чтобы установить безопасное соединение с хранилищем Windows Azure — рекомендуется.  
  
 Флажок**Сохранить мой ключ учетной записи**   
 Установите этот флажок, чтобы SQL Server запоминал ключ доступа для этой учетной записи хранения.  
  
### <a name="sql-credential"></a>Учетные данные SQL  
 **Выбор существующих учетных данных**  
 Выберите существующие учетные данные SQL, соответствующие учетной записи хранения и ключу доступа.  
  
 **Создание новых учетных данных**  
 Выберите этот параметр, чтобы создать новые учетные данные, используя учетную запись хранения и ключ доступа. Введите имя учетных данных в поле **Имя учетных данных** .  
  
  
