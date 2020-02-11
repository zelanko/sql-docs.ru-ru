---
title: Метод get_OLEDBCommand | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- get_OLEDBCommand method [ADO]
ms.assetid: 23d551f5-3d5b-434b-ade6-fef15f1710e7
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2d32d79b0a0481d2ade05a78c80d72587817a04b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67918575"
---
# <a name="get_oledbcommand-method"></a>Метод get_OLEDBCommand
Возвращает базовую команду OLE DB, которая сначала распространяет все сведения о параметрах, заданные в команде ADO, в команду OLE DB.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
HRESULT get_OLEDBCommand(  
      IUnknown **ppOLEDBCommand  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 *пполедбкомманд*  
 заполняет Указатель на расположение указателя, в котором будет записан указатель IUnknown для базовой OLE DBной команды.  
  
## <a name="applies-to"></a>Применяется к  
 [иадокоммандконструктион](https://msdn.microsoft.com/d8e54333-00eb-4b72-bf4a-ca92c7ca5f86)
