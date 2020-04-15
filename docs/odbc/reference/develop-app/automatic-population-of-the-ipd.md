---
title: Автоматическое население ИПД Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- automatically populating ipd [ODBC]
- descriptors [ODBC], automatically populating ipd
- descriptors [ODBC], allocating and freeing
- ipd [ODBC]
- allocating and freeing descriptors [ODBC]
ms.assetid: 1184a7d8-d557-4140-843b-6633ae6deacc
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1998ea1992ee7f14d87d01e348d955b017166088
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81285074"
---
# <a name="automatic-population-of-the-ipd"></a>Автоматическое заполнение IPD
Некоторые драйверы способны устанавливать поля IPD после подготовки параметризированного запроса. Поля дескриптора автоматически заполняются информацией о параметре, включая тип данных, точность, масштаб и другие характеристики. Это эквивалентно поддержке **S'LDescribeParam**. Эта информация может быть особенно ценной для приложения, когда у него нет другого способа обнаружить ее, например, когда специальный запрос выполняется с параметрами, о которыми приложение не знает.  
  
 Приложение определяет, поддерживает ли драйвер автоматическое население, позвонив в **S'LGetConnectAttr** с *атрибутом* SQL_ATTR_AUTO_IPD. Если SQL_TRUE возвращается, драйвер поддерживает его, и приложение может включить его, установив атрибут SQL_ATTR_ENABLE_AUTO_IPD оператора на SQL_TRUE.  
  
 При поддержке и включении автоматической популяции драйвер заполняет поля IPD после того, как заявление S'L, содержащее параметры, было подготовлено вызовом в **S'LPrepare.** Приложение может получить эту информацию, позвонив по телефону **S'LGetDesccField** или **S'LGetDesccRec**, или **S'LDescribeParam**. Приложение может использовать эту информацию для привязки наиболее подходящего буфера приложения к параметру или для указания преобразования данных для него.  
  
 Автоматическое население ИПД может привести к штрафу за выполнение работ. Приложение может отключить его, сбросив атрибут SQL_ATTR_ENABLE_AUTO_IPD оператора на SQL_FALSE (значение по умолчанию).
