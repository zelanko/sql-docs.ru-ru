---
description: Метод get_OLEDBCommand
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 56148afcd3c7d3e18e856c6e50a44f35aaa1bc64
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88775133"
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
  
## <a name="applies-to"></a>Применение  
 [иадокоммандконструктион](/previous-versions/windows/desktop/aa965677(v=vs.85))