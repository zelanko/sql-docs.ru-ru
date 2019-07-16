---
title: Служба курсора Майкрософт для OLE DB | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- cursor service for ole db [ADO]
- cursors [ADO], cursor service for OLE DB
ms.assetid: 1ac3bd9b-2d45-4cc8-88ec-bd8a218cfb49
author: MightyPen
ms.author: genemi
ms.openlocfilehash: aeac8c848f01f01e8969f94c571ad15f5e7f615a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67923911"
---
# <a name="the-microsoft-cursor-service-for-ole-db"></a>Служба курсора Майкрософт для OLE DB
При выборе клиентский курсор, или задать **CursorLocation** свойства **adUseClient**, вызываемом служба курсора Майкрософт для OLE DB. Может также появиться ссылки на «Обработчик курсора клиента», который является по сути то же самое в контексте ADO. Эта служба дополняет поддержка курсоров функции поставщиков данных. Таким образом может воспринимать относительно однообразного функциональные возможности из всех поставщиков данных.  
  
 Служба курсора для OLE DB доступны динамические свойства и расширяет поведение определенных методов. Например **оптимизировать** динамических свойств включает создание временных индексов для упрощения некоторых операций, таких как **найти** метод.  
  
 Служба курсора включает поддержку пакетного обновления во всех случаях. Также эта система симулирует более мощным типов курсора, таких как динамические курсоры, когда поставщик данных можно передавать только меньшими возможностями курсоры, таких как статические курсоры.  
  
## <a name="see-also"></a>См. также  
 [Служба курсора Майкрософт для OLE DB (компонент службы ADO)](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md)
