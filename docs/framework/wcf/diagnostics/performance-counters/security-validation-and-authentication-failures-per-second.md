---
title: Falhas de autenticação e validação de segurança por segundo
ms.date: 03/30/2017
ms.assetid: 266c3bd3-2ffc-4471-94b7-3675443be1ac
author: BrucePerlerMS
ms.openlocfilehash: 01fb7afd363e85e9c9ac5625175f350c00f66f26
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47204486"
---
# <a name="security-validation-and-authentication-failures-per-second"></a>Falhas de autenticação e validação de segurança por segundo
Nome do contador: validação de segurança e autenticação de falhas por segundo.  
  
## <a name="description"></a>Descrição  
 Esse contador é incrementado sempre que uma mensagem foi rejeitada devido a um problema de segurança não coberto pelo contador "Chamadas de segurança não autorizado". Esses problemas incluem:  
  
-   Não é possível ler o token de cliente da mensagem.  
  
-   Token de cliente falha na autenticação (por exemplo, senha incorreta).  
  
-   Falha na verificação de assinatura (por exemplo, a mensagem foi violada).  
  
-   A mensagem é uma duplicata da anterior, o que pode ocorrer durante um ataque de repetição.  
  
-   Ocorreu uma falha de descriptografia.  
  
-   Alguns necessários elementos (por exemplo, carimbo de hora ausente ou bloquear os dados criptografados) estão ausentes da mensagem.  
  
-   Ocorreram erros durante o handshake TLSNEGO/SPNEGO.  
  
 Esse contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), cujo valor é calculado usando a fórmula a seguir:  
  
 (N1-N0)/((D1-D0)/F)
