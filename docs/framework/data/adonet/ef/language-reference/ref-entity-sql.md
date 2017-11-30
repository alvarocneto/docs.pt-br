---
title: REF (Entity SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c5f4cb35-69e9-44cc-b63b-ee38922bbda1
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: dfc91b60c68f55def8e7f81c2c5dd068c23f6e69
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ref-entity-sql"></a><span data-ttu-id="82b24-102">REF (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="82b24-102">REF (Entity SQL)</span></span>
<span data-ttu-id="82b24-103">Retorna uma referência a uma instância de entidade.</span><span class="sxs-lookup"><span data-stu-id="82b24-103">Returns a reference to an entity instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82b24-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="82b24-104">Syntax</span></span>  
  
```  
REF( expression )   
```  
  
## <a name="arguments"></a><span data-ttu-id="82b24-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="82b24-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="82b24-106">Qualquer expressão válida que produzir uma instância de um tipo de objeto.</span><span class="sxs-lookup"><span data-stu-id="82b24-106">Any valid expression that yields an instance of an entity type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="82b24-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="82b24-107">Return Value</span></span>  
 <span data-ttu-id="82b24-108">Uma referência à instância de entidade especificada.</span><span class="sxs-lookup"><span data-stu-id="82b24-108">A reference to the specified entity instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="82b24-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="82b24-109">Remarks</span></span>  
 <span data-ttu-id="82b24-110">Uma referência de entidade consiste da chave de entidade e um nome de conjunto de entidades.</span><span class="sxs-lookup"><span data-stu-id="82b24-110">An entity reference consists of the entity key and an entity set name.</span></span> <span data-ttu-id="82b24-111">Porque os conjuntos de entidades diferentes podem ser baseados no mesmo tipo de entidade, uma chave específica de entidade pode aparecer em vários conjuntos de entidades.</span><span class="sxs-lookup"><span data-stu-id="82b24-111">Because different entity sets can be based on the same entity type, a particular entity key can appear in multiple entity sets.</span></span> <span data-ttu-id="82b24-112">No entanto, uma referência de entidade é sempre exclusivo.</span><span class="sxs-lookup"><span data-stu-id="82b24-112">However, an entity reference is always unique.</span></span> <span data-ttu-id="82b24-113">Se a expressão de entrada representa um objeto armazenado, uma referência a essa entidade será retornada.</span><span class="sxs-lookup"><span data-stu-id="82b24-113">If the input expression represents a persisted entity, a reference to this entity will be returned.</span></span> <span data-ttu-id="82b24-114">Se a expressão de entrada não é uma entidade armazenado, uma referência nula será retornada.</span><span class="sxs-lookup"><span data-stu-id="82b24-114">If the input expression is not a persisted entity, a null reference will be returned.</span></span>  
  
 <span data-ttu-id="82b24-115">Se o operador de extração de propriedade (.) é usada para acessar uma propriedade de uma entidade, a referência é desreferenciada automaticamente.</span><span class="sxs-lookup"><span data-stu-id="82b24-115">If the property extraction operator (.) is used to access a property of an entity, the reference is automatically dereferenced.</span></span>  
  
## <a name="example"></a><span data-ttu-id="82b24-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="82b24-116">Example</span></span>  
 <span data-ttu-id="82b24-117">A seguinte consulta SQL Entity usa o operador de referência para retornar a referência para um argumento de entidade de entrada.</span><span class="sxs-lookup"><span data-stu-id="82b24-117">The following Entity SQL query uses the REF operator to return the reference for an input entity argument.</span></span> <span data-ttu-id="82b24-118">A mesma consulta desreferencia a referência porque estamos usando uma operação de extração de propriedade (.) para acessar uma propriedade de entidade do produto.</span><span class="sxs-lookup"><span data-stu-id="82b24-118">The same query dereferences the reference because we are using a property extraction operation (.) to access a property of the Product entity.</span></span> <span data-ttu-id="82b24-119">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="82b24-119">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="82b24-120">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="82b24-120">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="82b24-121">Siga o procedimento [como: executar uma consulta que retorna resultados de PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="82b24-121">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2.  <span data-ttu-id="82b24-122">Passe a consulta a seguir como um argumento para o método `ExecutePrimitiveTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="82b24-122">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#REF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#ref)]  
  
## <a name="see-also"></a><span data-ttu-id="82b24-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="82b24-123">See Also</span></span>  
 [<span data-ttu-id="82b24-124">DEREF</span><span class="sxs-lookup"><span data-stu-id="82b24-124">DEREF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)  
 [<span data-ttu-id="82b24-125">CREATEREF</span><span class="sxs-lookup"><span data-stu-id="82b24-125">CREATEREF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)  
 [<span data-ttu-id="82b24-126">CHAVE</span><span class="sxs-lookup"><span data-stu-id="82b24-126">KEY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md)  
 [<span data-ttu-id="82b24-127">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="82b24-127">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="82b24-128">Definições de tipo</span><span class="sxs-lookup"><span data-stu-id="82b24-128">Type Definitions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/type-definitions-entity-sql.md)