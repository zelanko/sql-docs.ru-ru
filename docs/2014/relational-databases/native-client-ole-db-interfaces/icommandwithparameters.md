---
title: ICommandWithParameters | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 66644c70-def7-46d8-8c47-b883292a0288
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ea85e526d99e586c2534eee8ab83c6ddc66939db
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62643249"
---
# <a name="icommandwithparameters"></a>ICommandWithParameters
  Улучшения в ядре СУБД, начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Allow ICommandWithParameters:: GetParameterInfo, позволяют получить более точные описания ожидаемых результатов. Эти более точные результаты могут отличаться от значений, возвращаемых функцией Коммандвиспараметерс:: GetParameterInfo в предыдущих версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в разделе [Обнаружение метаданных](../native-client/features/metadata-discovery.md).  
  
 Кроме того, начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] при вызове интерфейса ICommandWithParameters::SetParameterInfo значение, передаваемое параметру *pwszName*, должно быть допустимым идентификатором. Дополнительные сведения см. в разделе [Идентификаторы баз данных](../databases/database-identifiers.md).  
  
## <a name="see-also"></a>См. также:  
 [Интерфейсы &#40;OLE DB&#41;](../../database-engine/dev-guide/interfaces-ole-db.md)  
  
  
