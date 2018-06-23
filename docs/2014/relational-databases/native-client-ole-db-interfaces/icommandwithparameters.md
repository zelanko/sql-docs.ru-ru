---
title: ICommandWithParameters | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 66644c70-def7-46d8-8c47-b883292a0288
caps.latest.revision: 6
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: edcba0cfc8ca284fd046f787829af4ba73dd366b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36194010"
---
# <a name="icommandwithparameters"></a>ICommandWithParameters
  Улучшения в ядро базы данных, начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] разрешить ICommandWithParameters::GetParameterInfo получать более точные описания ожидаемых результатов. Эти более точные результаты могут отличаться от значения, возвращаемые методом CommandWithParameters::GetParameterInfo в предыдущих версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в разделе [обнаружение метаданных](../native-client/features/metadata-discovery.md).  
  
 Кроме того, начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], при вызове метода ICommandWithParameters::SetParameterInfo значение, передаваемое *pwszName* параметр должен быть допустимым идентификатором. Дополнительные сведения см. в разделе [Идентификаторы баз данных](../databases/database-identifiers.md).  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы &#40;OLE DB&#41;](../../database-engine/dev-guide/interfaces-ole-db.md)  
  
  