---
title: Установка РасширенныйАнсиСЗЛ (ru) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- extendedANSISQL [ODBC], setting
ms.assetid: 37b775d1-65ac-45ac-8572-454bc4e3c1a2
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6b5c2e4ed4d8bd64d02fb6a62861db832f6b0898
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300804"
---
# <a name="setting-extendedansisql"></a>Настройка ExtendedAnsiSQL
Атрибут можно контролировать в строке соединения, добавляя атрибут ExtendedAnsiS'L:  
  
|Значение|Описание|  
|-----------|-----------------|  
|РасширенныйАнсиСЗЛЗ0 (по умолчанию)|Эта настройка не позволяет новым функциям.|  
|РасширенныйАнсиСЗЛNo|Эта настройка позволяет использовать новые функции.|  
  
 Атрибут также может быть установлен в DSN через диалоговую коробку **Advanced Options** при настройке DSN через панель управления.  
  
 Установка атрибута до 0 отсутчает новые функции; установка его на 1 позволяет новые функции.  
  
 Атрибут также может быть установлен с помощью S'LSetConnectAttr(). Значение атрибута составляет 65501 и устанавливается на значение S'LINTEGER 1 или 0, как это описано в предыдущей таблице. Его можно вызывать до или после подключения, но лучше вызвать его после подключения из-за порядка, в котором водитель обрабатывает атрибуты кэшированного соединения и строки соединения.
