---
title: Поддержка FOR XML для определяемых пользователем типов данных | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- UDTs [SQL Server], XML
- user-defined types [SQL Server], XML
ms.assetid: 354e2150-fa2a-4583-b1aa-6b78ae4378b6
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 275c6a13b0351bfa95e3d9ac642b1300f88e5c22
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48086184"
---
# <a name="for-xml-support-for-the-user-defined-data-types-udt"></a>Поддержка FOR XML для определяемых пользователем типов данных
  FOR XML не поддерживает определяемые пользователем типы данных (UDT) среды CLR.  
  
 Чтобы использовать FOR XML с определяемыми пользователем типами данных среды CRL, убедитесь, что у этих типов данных имеется XML-сериализация, а в предложении SELECT FOR XML используйте явное приведение к типу XML.  
  
## <a name="see-also"></a>См. также  
 [Поддержка FOR XML для различных типов данных SQL Server](for-xml-support-for-various-sql-server-data-types.md)  
  
  
