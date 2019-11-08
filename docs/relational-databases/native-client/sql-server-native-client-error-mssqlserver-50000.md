---
title: MSSQLSERVER_50000 | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- 50000 [SQL Server Native Client setup error]
ms.assetid: 5426d87a-d5d9-4984-b211-b07d69e834a2
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 60c0d0b594c8526d5106dd554652dce45f945585
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2019
ms.locfileid: "73759721"
---
# <a name="sql-server-native-client-error-mssqlserver_50000"></a>Ошибки собственного клиента SQL Server MSSQLSERVER_50000
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Номер версии продукта|11.0|  
|Идентификатор события|50000|  
|Источник события|SETUP|  
|Компонент|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client|  
|Символическое имя||  
|Текст сообщения|Произошла сетевая ошибка при попытке чтения из файла «%.*ls».|  
  
## <a name="explanation"></a>Объяснение  
 Была сделана попытка установить (или обновить) собственный клиент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на компьютер, где собственный клиент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] уже установлен и где существующая установка производилась из MSI-файла, который был переименован из sqlncli.msi.  
  
## <a name="user-action"></a>Действие пользователя  
 Для разрешения этой ошибки удалите существующую версию собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Чтобы предотвратить эту ошибку, не устанавливайте собственный клиент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] из MSI-файла, который не называется sqlncli.msi.  
  
## <a name="internal-only"></a>Только для внутреннего использования  
  
