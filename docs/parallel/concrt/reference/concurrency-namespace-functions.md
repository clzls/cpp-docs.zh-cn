---
title: 并发命名空间函数 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- concrt/concurrency::Alloc
- concrt/concurrency::DisableTracing
- concrt/concurrency::EnableTracing
- concrtrm/concurrency::GetExecutionContextId
- concrtrm/concurrency::GetOSVersion
- concrtrm/concurrency::GetProcessorNodeCount
- concrtrm/concurrency::GetSchedulerId
- agents/concurrency::asend
- ppltasks/concurrency::cancel_current_task
- ppltasks/concurrency::create_async
- ppltasks/concurrency::create_task
- concurrent_vector/concurrency::internal_assign_iterators
- ppl/concurrency::interruption_point
- agents/concurrency::make_choice
- agents/concurrency::make_greedy_join
- ppl/concurrency::make_task
- ppl/concurrency::parallel_buffered_sort
- ppl/concurrency::parallel_for_each
- ppl/concurrency::parallel_invoke
- ppl/concurrency::parallel_reduce
- ppl/concurrency::parallel_sort
- agents/concurrency::receive
- ppl/concurrency::run_with_cancellation_token
- pplconcrt/concurrency::set_ambient_scheduler
- concrt/concurrency::set_task_execution_resources
- ppltasks/concurrency::task_from_exception
- ppltasks/concurrency::task_from_result
- concrt/concurrency::wait
- ppltasks/concurrency::when_all
- ppltasks/concurrency::when_any
dev_langs:
- C++
ms.assetid: 520a6dff-9324-4df2-990d-302e3050af6a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9e1eed6fdbf5f676e5a7177affb7c38cd016fa4c
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="concurrency-namespace-functions"></a>并发命名空间函数
||||  
|-|-|-|  
|[Alloc](#alloc)|[CreateResourceManager](#createresourcemanager)|[DisableTracing](#disabletracing)|  
|[EnableTracing](#enabletracing)|[可用](#free)|[GetExecutionContextId](#getexecutioncontextid)|  
|[GetOSVersion](#getosversion)|[GetProcessorCount](#getprocessorcount)|[GetProcessorNodeCount](#getprocessornodecount)|  
|[GetSchedulerId](#getschedulerid)|[Trace_agents_register_name](#trace_agents_register_name)|[asend](#asend)|  
|[cancel_current_task](#cancel_current_task)|[clear](#clear)|[create_async](#create_async)|  
|[create_task](#create_task)|[get_ambient_scheduler](#get_ambient_scheduler)|[internal_assign_iterators](#internal_assign_iterators)|  
|[interruption_point](#interruption_point)|[is_current_task_group_canceling](#is_current_task_group_canceling)|[make_choice](#make_choice)|  
|[make_greedy_join](#make_greedy_join)|[make_join](#make_join)|[make_task](#make_task)|  
|[parallel_buffered_sort](#parallel_buffered_sort)|[parallel_for](#parallel_for)|[parallel_for_each](#parallel_for_each)|  
|[parallel_invoke](#parallel_invoke)|[parallel_radixsort](#parallel_radixsort)|[parallel_reduce](#parallel_reduce)|  
|[parallel_sort](#parallel_sort)|[parallel_transform](#parallel_transform)|[receive](#receive)|  
|[run_with_cancellation_token](#run_with_cancellation_token)|[发送](#send)|[set_ambient_scheduler](#set_ambient_scheduler)|  
|[set_task_execution_resources](#set_task_execution_resources)|[swap](#swap)|[task_from_exception](#task_from_exception)|  
|[task_from_result](#task_from_result)|[try_receive](#try_receive)|[等待](#wait)|  
|[when_all](#when_all)|[when_any](#when_any)|  
  
##  <a name="alloc"></a>  Alloc  
 通过并发运行时缓存子分配器分配具有指定大小的内存块。  
  
```
void* __cdecl Alloc(size_t _NumBytes);
```  
  
### <a name="parameters"></a>参数  
 `_NumBytes`  
 要分配的内存的字节数。  
  
### <a name="return-value"></a>返回值  
 指向新分配内存的指针。  
  
### <a name="remarks"></a>备注  
 有关哪些应用程序中的方案适合使用缓存子分配器的详细信息，请参阅[任务计划程序](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)。  
  
##  <a name="asend"></a>  asend  
 异步发送操作，计划任务以将数据传播到目标块。  
  
```
template <class T>
bool asend(
    _Inout_ ITarget<T>* _Trg,
    const T& _Data);

template <class T>
bool asend(
    ITarget<T>& _Trg,
    const T& _Data);
```  
  
### <a name="parameters"></a>参数  
 `T`  
 要发送的数据的类型。  
  
 `_Trg`  
 指针或数据发送到的 target 引用。  
  
 `_Data`  
 对要发送的数据的引用。  
  
### <a name="return-value"></a>返回值  
 `true` 如果消息已被接受之前该方法返回，`false`否则为。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[消息传递函数](../../../parallel/concrt/message-passing-functions.md)。  
  
##  <a name="cancel_current_task"></a>  cancel_current_task  
 获取当前执行的任务。 此函数可从任务主体中进行调用，以便中止任务的执行并使其进入 `canceled` 状态。  
  
 不支持从 `task` 主体外部调用此函数的情况。 这样做将导致未定义的行为，例如应用程序崩溃或挂起。  
  
```
inline __declspec(noreturn) void __cdecl cancel_current_task();
```  
  
##  <a name="clear"></a>  清除  
 清除并发队列，销毁所有当前排队元素。 此方法不是并发安全。  
  
```
template<typename T, class _Ax>
void concurrent_queue<T, _Ax>::clear();
```   
  
### <a name="parameters"></a>参数  
 `T`  
 `_Ax`  
  
##  <a name="create_async"></a>  create_async  
 基于用户提供的 lambda 或函数对象创建 Windows 运行时异步构造。 `create_async` 的返回类型是基于传递给方法的 lambda 的签名的 `IAsyncAction^`、`IAsyncActionWithProgress<TProgress>^`、`IAsyncOperation<TResult>^` 或 `IAsyncOperationWithProgress<TResult, TProgress>^` 之一。  
  
```
template<typename _Function>
__declspec(noinline) auto create_async(const _Function& _Func)
    -> decltype(ref new details::_AsyncTaskGeneratorThunk<_Function>(_Func));
```  
  
### <a name="parameters"></a>参数  
 `_Function`  
 `_Func`  
 从其中创建 Windows 运行时异步构造的 lambda 或函数对象。  
  
### <a name="return-value"></a>返回值  
 一个异步构造，它由 IAsyncAction ^，IAsyncActionWithProgress\<TProgress > ^，IAsyncOperation\<TResult > ^，或 IAsyncOperationWithProgress\<TResult，TProgress > ^。 返回的接口依赖于传递给函数的 lambda 的签名。  
  
### <a name="remarks"></a>备注  
 lambda 的返回类型确定该构造是一个行为还是一项操作。  
  
 返回 void 的 lambda 将导致创建一些行为。 返回类型为 `TResult` 的结果的 lambda 将导致创建 TResult 的操作。  
  
 lambda 可能还返回 `task<TResult>`（在自身中封装异步工作或是表示异步工作的任务链的延续）。 在此示例中，由于任务是异步执行的，所以将以内联方式执行 lambda，并且将解包 lambda 的返回类型以生成 `create_async` 返回的异步构造。 这意味着 lambda 的返回任务\<void > 将导致创建一些操作，并返回一个任务的 lambda 的\<TResult > 将导致创建 TResult 的操作。  
  
 lambda 可采用零个、一个或两个自变量。 有效的参数是 `progress_reporter<TProgress>` 和 `cancellation_token`（此顺序为同时使用两个参数的顺序）。 无自变量的 lambda 将导致创建一个缺少进度报告功能的异步构造。 采用 progress_reporter 的 lambda\<TProgress > 将导致`create_async`返回一个异步构造将报告 TProgress 类型的进度每次`report`调用 progress_reporter 对象的方法。 采用 cancellation_token 的 lambda 可以使用该标记来检查取消情况，或将该标记传递给它创建的任务，以便取消异步构造可导致取消这些任务。  
  
 如果 lambda 或函数对象的主体返回一个结果 (并且不是\<TResult >)，将在任务运行时的上下文中的 MTA 隐式为其创建过程中以异步方式执行 lamdba。 `IAsyncInfo::Cancel` 方法将导致取消隐式任务。  
  
 如果 lambda 的主体返回一个任务，则 lamba 将通过声明 lambda 采用类型为 `cancellation_token` 的参数，以内联方式执行，您可以通过在创建任务时将此标记传入，从而触发对在 lambda 中创建的任何任务的取消。 您还可对此标记使用 `register_callback` 方法，以使运行时在您对产生的异步操作或行为调用 `IAsyncInfo::Cancel` 时调用回调。  
  
 此函数是仅可用于 Windows 运行时应用。  
  
##  <a name="createresourcemanager"></a>  CreateResourceManager  
 返回表示并发运行时的资源管理器的单一实例的接口。 资源管理器负责将资源分配给想要相互合作的计划程序。  
  
```
IResourceManager* __cdecl CreateResourceManager();
```  
  
### <a name="return-value"></a>返回值  
 一个 `IResourceManager` 接口。  
  
### <a name="remarks"></a>备注  
 多个后续调用此方法将返回相同的实例的资源管理器。 每次调用此方法会递增引用计数在资源管理器中，并必须通过调用匹配[iresourcemanager:: Release](http://msdn.microsoft.com/en-us/5d1356ec-fbd3-4284-a361-1e9e20bbb522)方法完成您的计划程序通信使用资源管理器。  
  
 [unsupported_os](unsupported-os-class.md)如果操作系统不支持并发运行时引发。  
  
##  <a name="create_task"></a>  create_task  
 创建 PPL[任务](http://msdn.microsoft.com/en-us/5389e8a5-5038-40b6-844a-55e9b58ad35f)对象。 在你会使用任务构造函数的任何位置都可以使用 `create_task`。 出于便利性提供该函数，因为它允许在创建任务时使用 `auto` 关键字。  
  
```
template<typename T>
__declspec(noinline) auto create_task(T _Param, const task_options& _TaskOptions = task_options())
    -> task<typename details::_TaskTypeFromParam<T>::T>;

template<typename _ReturnType>
__declspec( noinline) task<_ReturnType> create_task(const task<_ReturnType>& _Task);
```  
  
### <a name="parameters"></a>参数  
 `T`  
 从中构造任务的参数的类型。  
  
 `_ReturnType`  
 `_Param`  
 从中构造任务的参数。 这可能是一个 lambda 或函数对象，对象`task_completion_event`对象、 不同`task`对象或如果你要在 UWP 应用中使用任务 Windows::Foundation::IAsyncInfo 接口。  
  
 `_TaskOptions`  
 `_Task`  
  
### <a name="return-value"></a>返回值  
 类型的一个新任务`T`，即从推断`_Param`。  
  
### <a name="remarks"></a>备注  
 第一个重载的行为类似任务构造函数采用单个参数。  
  
 第二个重载将提供与新创建的任务的取消标记相关联。 如果你使用此重载则不允许在不同传递`task`对象作为第一个参数。  
  
 从第一个参数情况下，返回的任务的类型推断函数。 如果`_Param`是`task_completion_event<T>`、 `task<T>`，或返回任何一种类型的涵子`T`或`task<T>`，所创建的任务的类型是`task<T>`。  
  
 在 UWP 应用中，如果`_Param`属于类型 Windows::Foundation::IAsyncOperation\<T > ^ 或 Windows::Foundation::IAsyncOperationWithProgress\<T、 P > ^，或创建的任务将为返回这些类型的某个函数，类型`task<T>`。 如果`_Param`属于类型 Windows::Foundation::IAsyncAction ^ 或 Windows::Foundation::IAsyncActionWithProgress\<P > ^，或返回这些类型的某个函数，创建的任务将具有键入`task<void>`。  
  
##  <a name="disabletracing"></a>  DisableTracing  
 在并发运行时中禁用跟踪。 此函数被弃用，因为默认注销 ETW 跟踪。  
  
```
__declspec(deprecated("Concurrency::DisableTracing is a deprecated function.")) _CRTIMP HRESULT __cdecl DisableTracing();
```  
  
### <a name="return-value"></a>返回值  
 如果正确禁用跟踪，`S_OK`返回。 如果之前未启动跟踪，将返回 `E_NOT_STARTED`。  
  
##  <a name="enabletracing"></a>  EnableTracing  
 在并发运行时中启用跟踪。 此函数被弃用，因为现在默认启用 ETW 跟踪。  
  
```
__declspec(deprecated("Concurrency::EnableTracing is a deprecated function.")) _CRTIMP HRESULT __cdecl EnableTracing();
```  
  
### <a name="return-value"></a>返回值  
 如果正确启动跟踪，`S_OK`返回; 否则为`E_NOT_STARTED`返回。  
  
##  <a name="free"></a>  可用  
 释放先前通过 `Alloc` 方法分配给并发运行时的缓存子分配器的内存块。  
  
```
void __cdecl Free(_Pre_maybenull_ _Post_invalid_ void* _PAllocation);
```  
  
### <a name="parameters"></a>参数  
 `_PAllocation`  
 指向以前分配的内存的指针`Alloc`方法即被释放。 如果参数`_PAllocation`设置为值`NULL`，此方法将忽略它，然后立即返回。  
  
### <a name="remarks"></a>备注  
 有关哪些应用程序中的方案适合使用缓存子分配器的详细信息，请参阅[任务计划程序](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)。  
  
##  <a name="get_ambient_scheduler"></a>  get_ambient_scheduler  
  
```
inline std::shared_ptr<::Concurrency::scheduler_interface> get_ambient_scheduler();
```  
  
### <a name="return-value"></a>返回值  
  
##  <a name="getexecutioncontextid"></a>  GetExecutionContextId  
 返回可以分配给实现 `IExecutionContext` 接口的执行上下文的唯一标识符。  
  
```
unsigned int __cdecl GetExecutionContextId();
```  
  
### <a name="return-value"></a>返回值  
 执行上下文的唯一标识符。  
  
### <a name="remarks"></a>备注  
 使用此方法传递之前获取的执行上下文的标识符`IExecutionContext`作为参数传递给任何资源管理器提供的方法的接口。  
  
##  <a name="getosversion"></a>  GetOSVersion  
 返回操作系统版本。  
  
```
IResourceManager::OSVersion __cdecl GetOSVersion();
```  
  
### <a name="return-value"></a>返回值  
 一个枚举的值，表示操作系统。  
  
### <a name="remarks"></a>备注  
 [unsupported_os](unsupported-os-class.md)如果操作系统不支持并发运行时引发。  
  
##  <a name="getprocessorcount"></a>  GetProcessorCount  
 返回基础系统上的硬件线程数。  
  
```
unsigned int __cdecl GetProcessorCount();
```  
  
### <a name="return-value"></a>返回值  
 硬件线程数。  
  
### <a name="remarks"></a>备注  
 [unsupported_os](unsupported-os-class.md)如果操作系统不支持并发运行时引发。  
  
##  <a name="getprocessornodecount"></a>  GetProcessorNodeCount  
 返回基础系统上的 NUMA 节点数或处理器包数。  
  
```
unsigned int __cdecl GetProcessorNodeCount();
```  
  
### <a name="return-value"></a>返回值  
 NUMA 节点或处理器包数。  
  
### <a name="remarks"></a>备注  
 如果系统包含多个 NUMA 节点比处理器包，在返回 NUMA 节点的数目，否则，返回的处理器包的数量。  
  
 [unsupported_os](unsupported-os-class.md)如果操作系统不支持并发运行时引发。  
  
##  <a name="getschedulerid"></a>  GetSchedulerId  
 返回可以分配给实现 `IScheduler` 接口的计划程序的唯一标识符。  
  
```
unsigned int __cdecl GetSchedulerId();
```  
  
### <a name="return-value"></a>返回值  
 计划程序唯一标识符。  
  
### <a name="remarks"></a>备注  
 使用此方法来为您的计划程序获取的标识符之前传递,`IScheduler`作为参数传递给任何资源管理器提供的方法的接口。  
  
##  <a name="internal_assign_iterators"></a>  internal_assign_iterators  
  
```
template<typename T, class _Ax>
template<class _I> 
void concurrent_vector<T, _Ax>::internal_assign_iterators(
   _I first,
   _I last);
```   
  
### <a name="parameters"></a>参数  
 `T`  
 `_Ax`  
 `_I`  
 `first`  
 `last`  
  
##  <a name="interruption_point"></a>  interruption_point  
 创建取消的中断点。 如果正在调用此函数的上下文中执行取消操作，则此函数将引发内部异常，该内部异常中止当前执行并行工作的执行。 如果没有正在执行取消操作，则函数不执行任何操作。  
  
```
inline void interruption_point();
```  
  
### <a name="remarks"></a>备注  
 您不应捕捉由 `interruption_point()` 函数引发的内部取消异常。 此异常将由运行时捕捉和处理，捕捉它可能会导致程序行为异常。  
  
##  <a name="is_current_task_group_canceling"></a>  is_current_task_group_canceling  
 返回在当前上下文中进行内联执行的任务组是否正处于活动取消的过程中（或不久将取消）的指示。 请注意，如果当前上下文中没有当前正在进行内联执行的任务组，则将返回 `false`。  
  
```
bool __cdecl is_current_task_group_canceling();
```  
  
### <a name="return-value"></a>返回值  
 `true` 如果正在取消当前正在执行的任务组，`false`否则为。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[取消](../../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation)。  
  
##  <a name="make_choice"></a>  make_choice  
 从可选的 `choice` 或 `Scheduler` 及两个或更多输入源构造 `ScheduleGroup` 消息块。  
  
```
template<typename T1, typename T2, typename... Ts>
choice<std::tuple<T1, T2, Ts...>> make_choice(
    Scheduler& _PScheduler,
    T1  _Item1,
    T2  _Item2,
    Ts... _Items);

template<typename T1, typename T2, typename... Ts>
choice<std::tuple<T1, T2, Ts...>> make_choice(
    ScheduleGroup& _PScheduleGroup,
    T1  _Item1,
    T2  _Item2,
    Ts... _Items);

template<typename T1, typename T2, typename... Ts>
choice<std::tuple<T1, T2, Ts...>> make_choice(
    T1  _Item1,
    T2  _Item2,
    Ts... _Items);
```  
  
### <a name="parameters"></a>参数  
 `T1`  
 消息块的第一个源类型。  
  
 `T2`  
 第二个源消息块类型。  
  
 `_PScheduler`  
 在其中计划了 `Scheduler` 消息块的传播任务的 `choice` 对象。  
  
 `_Item1`  
 第一个源。  
  
 `_Item2`  
 第二个源。  
  
 `_Items`  
 其他源。  
  
 `_PScheduleGroup`  
 在其中计划了 `ScheduleGroup` 消息块的传播任务的 `choice` 对象。 所用 `Scheduler` 对象由该计划组提示。  
  
### <a name="return-value"></a>返回值  
 一个具有两个或更多输入源的 `choice` 消息块。  
  
##  <a name="make_greedy_join"></a>  make_greedy_join  
 从可选的 `greedy multitype_join` 或 `Scheduler` 及两个或更多输入源构造 `ScheduleGroup` 消息块。  
  
```
template<typename T1, typename T2, typename... Ts>
multitype_join<std::tuple<T1, T2, Ts...>,greedy> make_greedy_join(
    Scheduler& _PScheduler,
    T1 _Item1,
    T2 _Item2,
    Ts... _Items);

template<typename T1, typename T2, typename... Ts>
multitype_join<std::tuple<T1, T2, Ts...>, greedy> make_greedy_join(
    ScheduleGroup& _PScheduleGroup,
    T1 _Item1,
    T2 _Item2,
    Ts... _Items);

template<typename T1, typename T2, typename... Ts>
multitype_join<std::tuple<T1, T2, Ts...>, greedy> make_greedy_join(
    T1 _Item1,
    T2 _Items,
    Ts... _Items);
```  
  
### <a name="parameters"></a>参数  
 `T1`  
 消息块的第一个源类型。  
  
 `T2`  
 第二个源消息块类型。  
  
 `_PScheduler`  
 在其中计划了 `Scheduler` 消息块的传播任务的 `multitype_join` 对象。  
  
 `_Item1`  
 第一个源。  
  
 `_Item2`  
 第二个源。  
  
 `_Items`  
 其他源。  
  
 `_PScheduleGroup`  
 在其中计划了 `ScheduleGroup` 消息块的传播任务的 `multitype_join` 对象。 所用 `Scheduler` 对象由该计划组提示。  
  
### <a name="return-value"></a>返回值  
 一个具有两个或更多输入源的 `greedy multitype_join` 消息块。  
  
##  <a name="make_join"></a>  make_join  
 从可选的 `non_greedy multitype_join` 或 `Scheduler` 及两个或更多输入源构造 `ScheduleGroup` 消息块。  
  
```
template<typename T1, typename T2, typename... Ts>
multitype_join<std::tuple<T1, T2, Ts...>> 
    make_join(
 Scheduler& _PScheduler,
    T1 _Item1,
    T2 _Item2,
    Ts... _Items);

template<typename T1, typename T2, typename... Ts>
multitype_join<std::tuple<T1, T2, Ts...>> make_join(
 ScheduleGroup& _PScheduleGroup,
    T1 _Item1,
    T2 _Item2,
    Ts... _Items);

template<typename T1, typename T2, typename... Ts>
multitype_join<std::tuple<T1, T2, Ts...>> make_join(
    T1 _Item1,
    T2 _Item2,
    Ts... _Items);
```  
  
### <a name="parameters"></a>参数  
 `T1`  
 消息块的第一个源类型。  
  
 `T2`  
 第二个源消息块类型。  
  
 `_PScheduler`  
 在其中计划了 `Scheduler` 消息块的传播任务的 `multitype_join` 对象。  
  
 `_Item1`  
 第一个源。  
  
 `_Item2`  
 第二个源。  
  
 `_Items`  
 其他源。  
  
 `_PScheduleGroup`  
 在其中计划了 `ScheduleGroup` 消息块的传播任务的 `multitype_join` 对象。 所用 `Scheduler` 对象由该计划组提示。  
  
### <a name="return-value"></a>返回值  
 一个具有两个或更多输入源的 `non_greedy multitype_join` 消息块。  
  
##  <a name="make_task"></a>  make_task  
 用于创建 `task_handle` 对象的工厂方法。  
  
```
template <class _Function>
task_handle<_Function> make_task(const _Function& _Func);
```  
  
### <a name="parameters"></a>参数  
 `_Function`  
 将调用以执行所表示的工作的函数对象类型`task_handle`对象。  
  
 `_Func`  
 将调用来执行工作所表示的函数`task_handle`对象。 这可能是 lambda functor、 指向函数的指针或支持具有签名的函数调用运算符的版本的任何对象`void operator()()`。  
  
### <a name="return-value"></a>返回值  
 一个 `task_handle` 对象。  
  
### <a name="remarks"></a>备注  
 此函数很有用，当你需要创建`task_handle`对象使用 lambda 表达式，因为它允许您创建无需知道 lambda 函子的实际类型的对象。  
  
##  <a name="parallel_buffered_sort"></a>  parallel_buffered_sort  
 将指定范围中的元素按非降序顺序排列，或根据二元谓词指定的排序条件排列（以并行方式）。 此函数是基于比较、不稳定的就地排序，因此它与 `std::sort` 在语义上相似，但它需要 `O(n)` 附加空间，并需要待排序的元素进行默认初始化。  
  
```
template<typename _Random_iterator>
inline void parallel_buffered_sort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End);

template<typename _Allocator,
    typename _Random_iterator>
inline void parallel_buffered_sort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End);

template<typename _Allocator,
    typename _Random_iterator>
inline void parallel_buffered_sort(
    const _Allocator& _Alloc,
    const _Random_iterator& _Begin,
    const _Random_iterator& _End);

template<typename _Random_iterator,
    typename _Function>
inline void parallel_buffered_sort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End,
    const _Function& _Func,
    const size_t _Chunk_size = 2048);

template<typename _Allocator,
    typename _Random_iterator,
    typename _Function>
inline void parallel_buffered_sort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End,
    const _Function& _Func,
    const size_t _Chunk_size = 2048);

template<typename _Allocator,
    typename _Random_iterator,
    typename _Function>
inline void parallel_buffered_sort(
    const _Allocator& _Alloc,
    const _Random_iterator& _Begin,
    const _Random_iterator& _End,
    const _Function& _Func,
    const size_t _Chunk_size = 2048);
```  
  
### <a name="parameters"></a>参数  
 `_Random_iterator`  
 输入范围的迭代器类型。  
  
 `_Allocator`  
 C + + 标准库兼容的内存分配器的类型。  
  
 `_Function`  
 二进制比较器的类型。  
  
 `_Begin`  
 一种随机访问迭代器，用于寻址要排序的范围中第一个元素的位置。  
  
 `_End`  
 一种随机访问迭代器，用于定址要排序的范围中最后元素之后下一个元素的位置。  
  
 `_Alloc`  
 C + + 标准库兼容的内存分配器实例。  
  
 `_Func`  
 用户定义的谓词函数对象，定义排序中连续元素要满足的比较条件。 二元谓词采用两个参数，并且在满足时返回 `true`，未满足时返回 `false`。 该比较器函数必须对序列中的元素对进行严格弱排序。  
  
 `_Chunk_size`  
 最小大小的区块将拆分为两个区块用于并行执行。  
  
### <a name="remarks"></a>备注  
 所有重载都需要`n * sizeof(T)`附加空间，其中`n`是要排序的元素的数目和`T`是元素类型。 在大多数情况下 parallel_buffered_sort 将通过显示中的性能改进[parallel_sort](concurrency-namespace-functions.md)，并且你应使用它通过 parallel_sort 如果你有可用内存。  
  
 如果未提供二进制比较器`std::less`用作默认情况下，需要元素类型，以提供运算符`operator<()`。  
  
 如果未提供的分配器类型或实例，c + + 标准库内存分配器`std::allocator<T>`用于分配的缓冲区。  
  
 算法将输入范围分为两个区块，然后将每个区块分成两个以并行方式执行的子区块。 可选参数 `_Chunk_size` 可用于向算法指示它应按顺序处理区块的大小 <  `_Chunk_size`。  
  
##  <a name="parallel_for"></a>  parallel_for  
 `parallel_for` 循环访问某个索引范围，并在每次迭代时以并行方式执行用户提供的函数。  
  
```
template <typename _Index_type, typename _Function, typename _Partitioner>
void parallel_for(
    _Index_type first,
    _Index_type last,
    _Index_type _Step,
    const _Function& _Func,
    _Partitioner&& _Part);

template <typename _Index_type, typename _Function>
void parallel_for(
    _Index_type first,
    _Index_type last,
    _Index_type _Step,
    const _Function& _Func);

template <typename _Index_type, typename _Function>
void parallel_for(
    _Index_type first,
    _Index_type last,
    const _Function& _Func,
    const auto_partitioner& _Part = auto_partitioner());

template <typename _Index_type, typename _Function>
void parallel_for(
    _Index_type first,
    _Index_type last,
    const _Function& _Func,
    const static_partitioner& _Part);

template <typename _Index_type, typename _Function>
void parallel_for(
    _Index_type first,
    _Index_type last,
    const _Function& _Func,
    const simple_partitioner& _Part);

template <typename _Index_type, typename _Function>
void parallel_for(
    _Index_type first,
    _Index_type last,
    const _Function& _Func,
    affinity_partitioner& _Part);
```  
  
### <a name="parameters"></a>参数  
 `_Index_type`  
 所使用的迭代的索引的类型。  
  
 `_Function`  
 将在每次迭代执行函数的类型。  
  
 `_Partitioner`  
 用于分区提供的范围的分区的类型。  
  
 `first`  
 要包括在迭代中的第一个索引。  
  
 `last`  
 索引一超过要包括在迭代中的最后一个索引。  
  
 `_Step`  
 值，通过它来单步当循环从`first`到`last`。 步骤必须是正数。 [invalid_argument](../../../standard-library/invalid-argument-class.md)的一步是等于或大于 1 时引发。  
  
 `_Func`  
 要在每次迭代执行的函数。 这可能是 lambda 表达式、 函数指针，或支持具有签名的函数调用运算符的版本的任何对象`void operator()(_Index_type)`。  
  
 `_Part`  
 对分区程序对象的引用。 自变量可以是之一`const` [auto_partitioner](auto-partitioner-class.md)`&`， `const` [static_partitioner](static-partitioner-class.md)`&`， `const` [simple_分区程序](simple-partitioner-class.md)`&`或[affinity_partitioner](affinity-partitioner-class.md) `&`如果[affinity_partitioner](affinity-partitioner-class.md)使用对象，该引用必须是一个非常量的左值引用，以便算法可以存储供未来循环重用的状态。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[并行算法](../../../parallel/concrt/parallel-algorithms.md)。  
  
##  <a name="parallel_for_each"></a>  parallel_for_each  
 `parallel_for_each` 以并行方式将指定函数应用于某个范围内的每个元素。 除对元素并行执行迭代以及未指定迭代的顺序外，它在语义上等效于 `std` 命名空间中的 `for_each` 函数。 实际参数 `_Func` 必须支持窗体 `operator()(T)` 的函数调用运算符，其中形式参数 `T` 是正在被循环访问的容器的项类型。  
  
```
template <typename _Iterator, typename _Function>
void parallel_for_each(
    _Iterator first,
    _Iterator last,
    const _Function& _Func);

template <typename _Iterator, typename _Function, typename _Partitioner>
void parallel_for_each(
    _Iterator first,
    _Iterator last,
    const _Function& _Func,
    _Partitioner&& _Part);
```  
  
### <a name="parameters"></a>参数  
 `_Iterator`  
 用于循环访问容器的迭代器的类型。  
  
 `_Function`  
 将应用于范围内的每个元素的函数类型。  
  
 `_Partitioner`  
 `first`  
 寻址的迭代器的第一个元素的位置包括在并行迭代中。  
  
 `last`  
 寻址的迭代器的最后一个元素的位置包括在并行迭代中。  
  
 `_Func`  
 用户定义函数对象应用于范围中每个元素。  
  
 `_Part`  
 对分区程序对象的引用。 自变量可以是之一`const` [auto_partitioner](auto-partitioner-class.md)`&`， `const` [static_partitioner](static-partitioner-class.md)`&`， `const` [simple_分区程序](simple-partitioner-class.md)`&`或[affinity_partitioner](affinity-partitioner-class.md) `&`如果[affinity_partitioner](affinity-partitioner-class.md)使用对象，该引用必须是一个非常量的左值引用，以便算法可以存储供未来循环重用的状态。  
  
### <a name="remarks"></a>备注  
 [auto_partitioner](auto-partitioner-class.md)将用于而无需显式分区程序的重载。  
  
 对于不支持随机迭代器访问，仅[auto_partitioner](auto-partitioner-class.md)支持。  
  
 有关详细信息，请参阅[并行算法](../../../parallel/concrt/parallel-algorithms.md)。  
  
##  <a name="parallel_invoke"></a>  parallel_invoke  
 执行作为参数并行提供的函数对象，并在它们完成执行后进行阻止。 每个函数对象都可以是 lambda 表达式、函数指针或支持具有签名 `void operator()()` 的函数调用运算符的任何对象。  
  
```
template <typename _Function1, typename _Function2>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2);

template <typename _Function1, typename _Function2, typename _Function3>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3);

template <typename _Function1,
    typename _Function2,
    typename _Function3,
    typename _Function4>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3,
    const _Function4& _Func4);

template <typename _Function1,
    typename _Function2,
    typename _Function3,
    typename _Function4,
    typename _Function5>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3,
    const _Function4& _Func4,
    const _Function5& _Func5);

template <typename _Function1,
    typename _Function2,
    typename _Function3,
    typename _Function4,
    typename _Function5,
    typename _Function6>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3,
    const _Function4& _Func4,
    const _Function5& _Func5,
    const _Function6& _Func6);

template <typename _Function1,
    typename _Function2,
    typename _Function3,
    typename _Function4,
    typename _Function5,
    typename _Function6,
    typename _Function7>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3,
    const _Function4& _Func4,
    const _Function5& _Func5,
    const _Function6& _Func6,
    const _Function7& _Func7);

template <typename _Function1,
    typename _Function2,
    typename _Function3,
    typename _Function4,
    typename _Function5,
    typename _Function6,
    typename _Function7,
    typename _Function8>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3,
    const _Function4& _Func4,
    const _Function5& _Func5,
    const _Function6& _Func6,
    const _Function7& _Func7,
    const _Function8& _Func8);

template <typename _Function1,
    typename _Function2,
    typename _Function3,
    typename _Function4,
    typename _Function5,
    typename _Function6,
    typename _Function7,
    typename _Function8,
    typename _Function9>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3,
    const _Function4& _Func4,
    const _Function5& _Func5,
    const _Function6& _Func6,
    const _Function7& _Func7,
    const _Function8& _Func8,
    const _Function9& _Func9);

template <typename _Function1,
    typename _Function2,
    typename _Function3,
    typename _Function4,
    typename _Function5,
    typename _Function6,
    typename _Function7,
    typename _Function8,
    typename _Function9,
    typename _Function10>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3,
    const _Function4& _Func4,
    const _Function5& _Func5,
    const _Function6& _Func6,
    const _Function7& _Func7,
    const _Function8& _Func8,
    const _Function9& _Func9,
    const _Function10& _Func10);
```  
  
### <a name="parameters"></a>参数  
 `_Function1`  
 并行执行的第一个函数对象的类型。  
  
 `_Function2`  
 并行执行的第二个函数对象的类型。  
  
 `_Function3`  
 并行执行的第三个函数对象的类型。  
  
 `_Function4`  
 并行执行的第四个函数对象的类型。  
  
 `_Function5`  
 并行执行的第五个函数对象的类型。  
  
 `_Function6`  
 并行执行的第六个函数对象的类型。  
  
 `_Function7`  
 并行执行的第七个函数对象的类型。  
  
 `_Function8`  
 并行执行的第八个函数对象的类型。  
  
 `_Function9`  
 并行执行的第九个函数对象的类型。  
  
 `_Function10`  
 并行执行的第 10 个函数对象的类型。  
  
 `_Func1`  
 并行执行的第一个函数对象。  
  
 `_Func2`  
 若要并行执行第二个函数对象。  
  
 `_Func3`  
 并行执行的第三个函数对象。  
  
 `_Func4`  
 并行执行的第四个函数对象。  
  
 `_Func5`  
 并行执行的第五个函数对象。  
  
 `_Func6`  
 并行执行的第六个函数对象。  
  
 `_Func7`  
 并行执行的第七个函数对象。  
  
 `_Func8`  
 并行执行的第八个函数对象。  
  
 `_Func9`  
 并行执行的第九个函数对象。  
  
 `_Func10`  
 并行执行的第 10 个函数对象。  
  
### <a name="remarks"></a>备注  
 请注意，一个或多个函数对象作为提供参数可能会执行将在调用上下文的内联。  
  
 如果一个或多个函数对象作为参数传递给此函数引发了异常，运行时将选择其选择的此类异常之一，并将其传播到调用`parallel_invoke`。  
  
 有关详细信息，请参阅[并行算法](../../../parallel/concrt/parallel-algorithms.md)。  
  
##  <a name="parallel_radixsort"></a>  parallel_radixsort  
 使用基数排序算法将指定范围中的元素按非降序顺序排列。 这是一个稳定排序函数，它需要可以投影要按无符号整数键排序的元素的投影函数。 默认初始化对于待排序的元素是必须的。  
  
```
template<typename _Random_iterator>
inline void parallel_radixsort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End);

template<typename _Allocator, typename _Random_iterator>
inline void parallel_radixsort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End);

template<typename _Allocator, typename _Random_iterator>
inline void parallel_radixsort(
    const _Allocator& _Alloc,
    const _Random_iterator& _Begin,
    const _Random_iterator& _End);

template<typename _Random_iterator, typename _Function>
inline void parallel_radixsort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End,
    const _Function& _Proj_func,
    const size_t _Chunk_size = 256* 256);

template<typename _Allocator, typename _Random_iterator,
    typename _Function>
inline void parallel_radixsort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End,
    const _Function& _Proj_func,
    const size_t _Chunk_size = 256* 256);

template<typename _Allocator,
    typename _Random_iterator,
    typename _Function>
inline void parallel_radixsort(
    const _Allocator& _Alloc,
    const _Random_iterator& _Begin,
    const _Random_iterator& _End,
    const _Function& _Proj_func,
    const size_t _Chunk_size = 256* 256);
```  
  
### <a name="parameters"></a>参数  
 `_Random_iterator`  
 输入范围的迭代器类型。  
  
 `_Allocator`  
 C + + 标准库兼容的内存分配器的类型。  
  
 `_Function`  
 投影函数的类型。  
  
 `_Begin`  
 一种随机访问迭代器，用于寻址要排序的范围中第一个元素的位置。  
  
 `_End`  
 一种随机访问迭代器，用于定址要排序的范围中最后元素之后下一个元素的位置。  
  
 `_Alloc`  
 C + + 标准库兼容的内存分配器实例。  
  
 `_Proj_func`  
 将元素转换为整数值用户定义的投影函数对象。  
  
 `_Chunk_size`  
 最小大小的区块将拆分为两个区块用于并行执行。  
  
### <a name="remarks"></a>备注  
 所有重载都需要`n * sizeof(T)`附加空间，其中`n`是要排序的元素的数目和`T`是元素类型。 具有签名一元投影函子`I _Proj_func(T)`需要返回密钥在给定元素，其中`T`是元素类型和`I`是无符号的整数类型。  
  
 如果未提供的投影函数，只需返回的元素的默认投影函数适用于整数类型。 该函数将无法编译如果该元素不在缺少整数类型的投影函数。  
  
 如果未提供的分配器类型或实例，c + + 标准库内存分配器`std::allocator<T>`用于分配的缓冲区。  
  
 算法将输入范围分为两个区块，然后将每个区块分成两个以并行方式执行的子区块。 可选参数 `_Chunk_size` 可用于向算法指示它应按顺序处理区块的大小 <  `_Chunk_size`。  
  
##  <a name="parallel_reduce"></a>  parallel_reduce  
 通过计算连续部分和来计算指定范围中所有元素的和，或计算类似的通过指定的二元运算（而不是求和运算）获得的连续部分结果的结果（以并行方式）。 `parallel_reduce` 与 `std::accumulate` 在语义上相似，但它需要二元运算是关联的，并需要标识值（而不是初始值）。  
  
```
template<typename _Forward_iterator>
inline typename std::iterator_traits<_Forward_iterator>::value_type parallel_reduce(
    _Forward_iterator _Begin,
    _Forward_iterator _End,
    const typename std::iterator_traits<_Forward_iterator>::value_type& _Identity);

template<typename _Forward_iterator, typename _Sym_reduce_fun>
inline typename std::iterator_traits<_Forward_iterator>::value_type parallel_reduce(
    _Forward_iterator _Begin,
    _Forward_iterator _End,
    const typename std::iterator_traits<_Forward_iterator>::value_type& _Identity,
    _Sym_reduce_fun _Sym_fun);

template<typename _Reduce_type,
    typename _Forward_iterator,
    typename _Range_reduce_fun,
    typename _Sym_reduce_fun>
inline _Reduce_type parallel_reduce(
    _Forward_iterator _Begin,
    _Forward_iterator _End,
    const _Reduce_type& _Identity,
    const _Range_reduce_fun& _Range_fun,
    const _Sym_reduce_fun& _Sym_fun);
```  
  
### <a name="parameters"></a>参数  
 `_Forward_iterator`  
 输入范围的迭代器类型。  
  
 `_Sym_reduce_fun`  
 对称缩减函数的类型。 这必须是函数类型与签名`_Reduce_type _Sym_fun(_Reduce_type, _Reduce_type)`，其中 _Reduce_type 是相同的标识类型和减少的结果类型。 对于第三个重载，这应是与的输出类型一致`_Range_reduce_fun`。  
  
 `_Reduce_type`  
 输入将减少，它可以是不同的输入的元素类型的类型。 返回值和标识值将包含此类型。  
  
 `_Range_reduce_fun`  
 范围缩减函数的类型。 这必须是函数类型与签名`_Reduce_type _Range_fun(_Forward_iterator, _Forward_iterator, _Reduce_type)`，_Reduce_type 是相同的标识类型和减少的结果类型。  
  
 `_Begin`  
 输入迭代器寻址的范围中的第一个元素降低。  
  
 `_End`  
 寻址的最后一个元素之外要减少的范围内的一个位置的元素的输入迭代器。  
  
 `_Identity`  
 标识值`_Identity`的减少的结果类型与相同的类型以及`value_type`的第一个和第二个重载的迭代器。 对于第三个重载，标识值必须具有降低的结果类型与相同的类型，但可以不同于`value_type`迭代器。 它必须具有适当的值以便范围 reduction 运算符`_Range_fun`，当应用于各种类型的单个元素时`value_type`，标识值，其行为相似类型的值的类型强制转换`value_type`到标识类型。  
  
 `_Sym_fun`  
 中的第二个减少将使用对称函数。 有关详细信息，请参阅备注。  
  
 `_Range_fun`  
 将在减少的第一阶段中使用的函数。 有关详细信息，请参阅备注。  
  
### <a name="return-value"></a>返回值  
 减少结果。  
  
### <a name="remarks"></a>备注  
 若要执行并行缩减，该函数，请将分成区块基于供基础计划程序的辅助进程数的范围。 减少分两个阶段进行，第一阶段执行的每个区块中减少并第二个阶段执行从每个区块的部分结果之间的减少。  
  
 第一个重载都需要的迭代器的`value_type`， `T`，作为标识值类型，以及减少结果类型是相同。 元素类型 T 必须提供运算符`T T::operator + (T)`以减少在每个块区中的元素。 在第二个阶段使用相同的运算符。  
  
 第二个重载还要求的迭代器`value_type`相同作为标识值类型，以及减少结果类型。 提供的二进制运算符`_Sym_fun`在这两个缩减阶段，标识值与第一阶段的初始值中使用。  
  
 对于第三个重载，标识值类型必须是相同为减少结果类型，但迭代器的`value_type`可能从这两个不同。 范围缩减函数`_Range_fun`在带有标识值的第一个阶段中使用的初始值和二元函数作为`_Sym_reduce_fun`应用到子在第二个阶段的结果。  
  
##  <a name="parallel_sort"></a>  parallel_sort  
 将指定范围中的元素按非降序顺序排列，或根据二元谓词指定的排序条件排列（以并行方式）。 此函数是基于比较、不稳定的就地排序，因此它与 `std::sort` 在语义上相似。  
  
```
template<typename _Random_iterator>
inline void parallel_sort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End);

template<typename _Random_iterator,typename _Function>
inline void parallel_sort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End,
    const _Function& _Func,
    const size_t _Chunk_size = 2048);
```  
  
### <a name="parameters"></a>参数  
 `_Random_iterator`  
 输入范围的迭代器类型。  
  
 `_Function`  
 二元比较函子的类型。  
  
 `_Begin`  
 一种随机访问迭代器，用于寻址要排序的范围中第一个元素的位置。  
  
 `_End`  
 一种随机访问迭代器，用于定址要排序的范围中最后元素之后下一个元素的位置。  
  
 `_Func`  
 用户定义的谓词函数对象，定义排序中连续元素要满足的比较条件。 二元谓词采用两个参数，并且在满足时返回 `true`，未满足时返回 `false`。 该比较器函数必须对序列中的元素对进行严格弱排序。  
  
 `_Chunk_size`  
 最小大小的区块将拆分为两个区块用于并行执行。  
  
### <a name="remarks"></a>备注  
 第一个重载使用二进制比较器 `std::less`。  
  
 第二个重载使用提供的应具有签名 `bool _Func(T, T)`（其中 `T` 是输入范围中元素的类型）的二进制比较器。  
  
 算法将输入范围分为两个区块，然后将每个区块分成两个以并行方式执行的子区块。 可选参数 `_Chunk_size` 可用于向算法指示它应按顺序处理区块的大小 <  `_Chunk_size`。  
  
##  <a name="parallel_transform"></a>  parallel_transform  
 将指定的函数对象应用于源范围中的每个元素或两个源范围中的一对元素，并将函数对象的返回值复制到目标范围（以并行方式）。 此函数在语义上等效于 `std::transform`。  
  
```
template <typename _Input_iterator1,
    typename _Output_iterator,
    typename _Unary_operator>
_Output_iterator parallel_transform(
    _Input_iterator1 first1,
    _Input_iterator1 last1,
    _Output_iterator _Result,
    const _Unary_operator& _Unary_op,
    const auto_partitioner& _Part = auto_partitioner());

template <typename _Input_iterator1,
    typename _Output_iterator,
    typename _Unary_operator>
_Output_iterator parallel_transform(
    _Input_iterator1 first1,
    _Input_iterator1 last1,
    _Output_iterator _Result,
    const _Unary_operator& _Unary_op,
    const static_partitioner& _Part);

template <typename _Input_iterator1,
    typename _Output_iterator,
    typename _Unary_operator>
_Output_iterator parallel_transform(
    _Input_iterator1 first1,
    _Input_iterator1 last1,
    _Output_iterator _Result,
    const _Unary_operator& _Unary_op,
    const simple_partitioner& _Part);

template <typename _Input_iterator1,
    typename _Output_iterator,
    typename _Unary_operator>
_Output_iterator parallel_transform(
    _Input_iterator1 first1,
    _Input_iterator1 last1,
    _Output_iterator _Result,
    const _Unary_operator& _Unary_op,
    affinity_partitioner& _Part);

template <typename _Input_iterator1,
    typename _Input_iterator2,
    typename _Output_iterator,
    typename _Binary_operator,
    typename _Partitioner>
_Output_iterator parallel_transform(
    _Input_iterator1 first1,
    _Input_iterator1 last1,
    _Input_iterator2
 first2,
    _Output_iterator _Result,
    const _Binary_operator& _Binary_op,
    _Partitioner&& _Part);

template <typename _Input_iterator1,
    typename _Input_iterator2,
    typename _Output_iterator,
    typename _Binary_operator>
_Output_iterator parallel_transform(
    _Input_iterator1 first1,
    _Input_iterator1 last1,
    _Input_iterator2
 first2,
    _Output_iterator _Result,
    const _Binary_operator& _Binary_op);
```  
  
### <a name="parameters"></a>参数  
 `_Input_iterator1`  
 第一个或唯一输入迭代器的类型。  
  
 `_Output_iterator`  
 输出迭代器的类型。  
  
 `_Unary_operator`  
 在输入范围内每个元素上执行的一元函子的类型。  
  
 `_Input_iterator2`  
 第二个输入迭代器的类型。  
  
 `_Binary_operator`  
 在两个源范围的元素上成对执行的二元函子的类型。  
  
 `_Partitioner`  
 `first1`  
 一种输入迭代器，用于定址所操作的第一个或唯一的源范围内第一个元素的位置。  
  
 `last1`  
 一种输入迭代器，用于定址所操作的第一个或唯一的源范围内最后元素之后下一个元素的位置。  
  
 `_Result`  
 一种输出迭代器，用于定址目标范围内第一个元素的位置。  
  
 `_Unary_op`  
 用户定义的应用于源范围内每个元素的一元函数对象。  
  
 `_Part`  
 对分区程序对象的引用。 自变量可以是之一`const` [auto_partitioner](auto-partitioner-class.md)`&`， `const` [static_partitioner](static-partitioner-class.md)`&`， `const` [simple_分区程序](simple-partitioner-class.md)`&`或[affinity_partitioner](affinity-partitioner-class.md) `&`如果[affinity_partitioner](affinity-partitioner-class.md)使用对象，该引用必须是一个非常量的左值引用，以便算法可以存储供未来循环重用的状态。  
  
 `first2`  
 一种输入迭代器，用于定址所操作的第二个源范围内第一个元素的位置。  
  
 `_Binary_op`  
 用户定义的按向前顺序成对应用于两个源范围的二元函数对象。  
  
### <a name="return-value"></a>返回值  
 一种输出迭代器，用于寻址接收通过函数对象转换的输出元素的目标范围内最后元素之后下一个元素的位置。  
  
### <a name="remarks"></a>备注  
 [auto_partitioner](auto-partitioner-class.md)将用于无显式分区程序自变量的重载。  
  
 对于不支持随机迭代器访问，仅[auto_partitioner](auto-partitioner-class.md)支持。  
  
 采用参数 `_Unary_op` 的重载将一元函子应用于输入范围内的每个元素，从而将输入范围转换为输出范围。 `_Unary_op` 必须支持带有签名 `operator()(T)` 的函数调用运算符，签名中的 `T` 是要循环访问的范围的值类型。  
  
 采用参数 `_Binary_op` 的重载将二元函子分别应用于第一个输入范围内的一个元素和第二个输入范围内的一个元素，从而将两个输入范围转换为输出范围。 `_Binary_op` 必须支持具有签名 `operator()(T, U)` 的函数调用运算符，签名中的 `T`, `U` 是两个输入迭代器的值类型。  
  
 有关详细信息，请参阅[并行算法](../../../parallel/concrt/parallel-algorithms.md)。  
  
##  <a name="receive"></a>  接收  
 常规接收实现，允许上下文仅等待来自一个源的数据并筛选所接受的值。  
  
```
template <class T>
T receive(
    _Inout_ ISource<T>* _Src,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);

template <class T>
T receive(
    _Inout_ ISource<T>* _Src,
    typename ITarget<T>::filter_method const& _Filter_proc,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);

template <class T>
T receive(
    ISource<T>& _Src,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);

template <class T>
T receive(
    ISource<T>& _Src,
    typename ITarget<T>::filter_method const& _Filter_proc,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```  
  
### <a name="parameters"></a>参数  
 `T`  
 负载类型。  
  
 `_Src`  
 指针或对从中需要数据源的引用。  
  
 `_Timeout`  
 最大时间该方法应为其的数据，以毫秒为单位。  
  
 `_Filter_proc`  
 确定是否应接受消息的筛选器函数。  
  
### <a name="return-value"></a>返回值  
 来自源的负载类型的值。  
  
### <a name="remarks"></a>备注  
 如果参数`_Timeout`具有常量以外的值`COOPERATIVE_TIMEOUT_INFINITE`，异常[operation_timed_out](operation-timed-out-class.md)如果指定的时间量过期之前收到一条消息，将引发。 如果你想零长度超时，则应使用[try_receive](concurrency-namespace-functions.md)函数，而不是调用`receive`且超时为`0`（零），因为它效率更高并且未引发超时异常。  
  
 有关详细信息，请参阅[消息传递函数](../../../parallel/concrt/message-passing-functions.md)。  
  
##  <a name="run_with_cancellation_token"></a>  run_with_cancellation_token  
 在给定取消标记的上下文中立即同步执行函数对象。  
  
```
template<typename _Function>
void run_with_cancellation_token(
    const _Function& _Func,
    cancellation_token _Ct);
```  
  
### <a name="parameters"></a>参数  
 `_Function`  
 将会调用的函数对象的类型。  
  
 `_Func`  
 将会执行的函数对象。 此对象必须支持具有 void(void) 签名的函数调用运算符。  
  
 `_Ct`  
 将控制函数对象隐式取消的取消标记。 如果希望避免执行的函数被要取消的父任务组隐式取消，请使用 `cancellation_token::none()`。  
  
### <a name="remarks"></a>备注  
 取消 `cancellation_token` 时，将触发函数对象中的任何中断点。 如果父任务具有不同的标记或没有标记，则显式标记 `_Ct` 会将此 `_Func` 从父任务取消中隔离出来。  
  
##  <a name="send"></a>  发送  
 同步发送操作，它会一直等待，直到目标接受或拒绝消息。  
  
```
template <class T>
bool send(_Inout_ ITarget<T>* _Trg, const T& _Data);

template <class T>
bool send(ITarget<T>& _Trg, const T& _Data);
```  
  
### <a name="parameters"></a>参数  
 `T`  
 负载类型。  
  
 `_Trg`  
 指针或数据发送到的 target 引用。  
  
 `_Data`  
 对要发送的数据的引用。  
  
### <a name="return-value"></a>返回值  
 `true` 如果消息已被接受，`false`否则为。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[消息传递函数](../../../parallel/concrt/message-passing-functions.md)。  
  
##  <a name="set_ambient_scheduler"></a>  set_ambient_scheduler  
  
```
inline void set_ambient_scheduler(std::shared_ptr<::Concurrency::scheduler_interface> _Scheduler);
```  
  
### <a name="parameters"></a>参数  
 `_Scheduler`  
  
##  <a name="set_task_execution_resources"></a>  set_task_execution_resources  
 将并发运行时内部工作线程使用的执行资源限制为指定的关联集。  
  
 仅在创建资源管理器之前，或在两个资源管理器生存期之间调用此方法才是有效的。 只要资源管理器在调用时不存在，就可以多次调用它。 设置关联限制后，它仍然有效，直到对 `set_task_execution_resources` 方法的下一次有效调用。  
  
 提供的关联掩码不需要是进程关联掩码的子集。 如果需要，将更新过程关联。  
  
```
void __cdecl set_task_execution_resources(
    DWORD_PTR _ProcessAffinityMask);

void __cdecl set_task_execution_resources(
    unsigned short count,
    PGROUP_AFFINITY _PGroupAffinity);
```  
  
### <a name="parameters"></a>参数  
 `_ProcessAffinityMask`  
 限于并发运行时辅助线程使用的关联掩码。 仅在想要将并发运行时限制为当前处理器组的一部分时，在具有 64 个以上硬件线程的系统上使用此方法。 通常，应使用接受将组关联的数组作为参数的方法版本，以限制具有 64 个以上硬件线程的计算机上的关联。  
  
 `count`  
 数组中参数 `GROUP_AFFINITY` 指定的 `_PGroupAffinity` 项的数目。  
  
 `_PGroupAffinity`  
 `GROUP_AFFINITY` 项的数组。  
  
### <a name="remarks"></a>备注  
 该方法将引发[invalid_operation](invalid-operation-class.md)异常如果资源管理器是在调用它时，时间存在和[invalid_argument](../../../standard-library/invalid-argument-class.md)异常如果将指定的结果的关联中的空集资源。  
  
 应仅在具有 Windows 7 或更高版本的操作系统上使用接受组关联作为参数的方法版本。 否则为[invalid_operation](invalid-operation-class.md)引发异常。  
  
 调用此方法后以编程方式修改进程关联，将不会导致资源管理器重新计算限于其使用的关联。 因此，对进程关联的所有更改都应在调用此方法之前进行。  
  
##  <a name="swap"></a>  swap  
 交换两个 `concurrent_vector` 对象的元素。  
  
```
template<typename T, class _Ax>
inline void swap(
    concurrent_vector<T, _Ax>& _A,
    concurrent_vector<T, _Ax>& _B);
```  
  
### <a name="parameters"></a>参数  
 `T`  
 并发向量中存储的元素数据类型。  
  
 `_Ax`  
 并发向量分配器类型。  
  
 `_A`  
 其元素将要与并发向量交换的并发向量`_B`。  
  
 `_B`  
 提供要交换的元素的并发向量或其元素将要与并发向量交换的向量`_A`。  
  
### <a name="remarks"></a>备注  
 模板函数是一种算法专用的容器类`concurrent_vector`执行成员函数`_A`。 [concurrent_vector:: swap](concurrent-vector-class.md#swap)( `_B`)。 这些是由编译器进行的函数模板部分排序的实例。 模板函数以此种方式重载时，模板与函数调用的匹配并不唯一，随后编译器会选择此模板函数的最专用化版本。 模板函数的常规版本`template <class T> void swap(T&, T&)`，算法类的工作原理是分配且较慢的操作。 每个容器中的专用化版本速度快很多，因为专用化版本可适用于容器类的内部表示形式。  
  
 此方法不是并发安全。 你必须确保在调用此方法时，没有其他线程正在执行的并发向量中的任何一个的操作。  
  
##  <a name="task_from_exception"></a>  task_from_exception  
  
```
template<typename _TaskType, typename _ExType>
task<_TaskType> task_from_exception(
    _ExType _Exception,
    const task_options& _TaskOptions = task_options());
```  
  
### <a name="parameters"></a>参数  
 `_TaskType`  
 `_ExType`  
 `_Exception`  
 `_TaskOptions`  
  
### <a name="return-value"></a>返回值  
  
##  <a name="task_from_result"></a>  task_from_result  
  
```
template<typename T>
task<T> task_from_result(
    T _Param,
    const task_options& _TaskOptions = task_options());

inline task<bool> task_from_result(ool _Param);

inline task<void> task_from_result(
    const task_options& _TaskOptions = task_options());
```  
  
### <a name="parameters"></a>参数  
 `T`  
 `_Param`  
 `_TaskOptions`  
  
### <a name="return-value"></a>返回值  
  
##  <a name="trace_agents_register_name"></a>  Trace_agents_register_name  
 在 ETW 跟踪中将给定名称关联到消息块或代理。  
  
```
template <class T>
void Trace_agents_register_name(
    _Inout_ T* _PObject,
    _In_z_ const wchar_t* _Name);
```  
  
### <a name="parameters"></a>参数  
 `T`  
 对象的类型。 这通常是消息块或代理。  
  
 `_PObject`  
 指向在跟踪中命名的消息块或代理的指针。  
  
 `_Name`  
 给定对象的名称。  
  
##  <a name="try_receive"></a>  try_receive  
 常规尝试-接收实现，允许上下文仅查找来自一个源的数据并筛选所接受的值。 如果数据未就绪，则方法将返回 false。  
  
``` 
template <class T>
bool try_receive(_Inout_ ISource<T>* _Src, T& _value);

template <class T>
bool try_receive(
    _Inout_ ISource<T>* _Src,
    T& _value,
    typename ITarget<T>::filter_method const& _Filter_proc);

template <class T>
bool try_receive(ISource<T>& _Src, T& _value);

template <class T>
bool try_receive(
    ISource<T>& _Src,
    T& _value,
    typename ITarget<T>::filter_method const& _Filter_proc);
```  
  
### <a name="parameters"></a>参数  
 `T`  
 负载类型  
  
 `_Src`  
 指针或对从中需要数据源的引用。  
  
 `_value`  
 对在其中放置结果的位置的引用。  
  
 `_Filter_proc`  
 确定是否应接受消息的筛选器函数。  
  
### <a name="return-value"></a>返回值  
 A`bool`值，该值指示是否将负载置于中`_value`。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[消息传递函数](../../../parallel/concrt/message-passing-functions.md)。  
  
##  <a name="wait"></a>  等待  
 将当前上下文暂停指定的一段时间。  
  
```
void __cdecl wait(unsigned int _Milliseconds);
```  
  
### <a name="parameters"></a>参数  
 `_Milliseconds`  
 当前上下文应该暂停的毫秒数。 如果 `_Milliseconds` 参数设置为值 `0`，则当前上下文应在继续之前执行其他可运行的上下文。  
  
### <a name="remarks"></a>备注  
 如果在并发运行时计划程序上下文上调用此方法，计划程序将查找不同的上下文在基础资源上运行。 由于计划程序在本质上是合作的，此上下文不会正好在指定的毫秒数后继续。 如果计划程序正忙于执行不协作产生计划程序的其他任务，那么等待时间可能是无限期。  
  
##  <a name="when_all"></a>  when_all  
 创建一个任务，在作为自变量提供的所有任务成功完成后，此任务将成功完成。  
  
```
template <typename _Iterator>
auto when_all(
    _Iterator _Begin,
    _Iterator _End,
    const task_options& _TaskOptions = task_options()) -> 
    decltype (details::_WhenAllImpl<typename std::iterator_traits<_Iterator>::value_type::result_type,
    _Iterator>::_Perform(_TaskOptions, _Begin,  _End));
```   
  
### <a name="parameters"></a>参数  
 `_Iterator`  
 输入迭代器的类型。  
  
 `_Begin`  
 要合并到结果任务的元素范围中第一个元素的位置。  
  
 `_End`  
 超出要合并到结果任务的元素范围的第一个元素的位置。  
  
 `_TaskOptions`  
  
### <a name="return-value"></a>返回值  
 将在所有输入任务成功完成后成功完成的任务。 如果输入任务的类型为 `T`，则此函数的输出将为 `task<std::vector<T>>`。 如果输入任务的类型为 `void`，则输出任务也将是 `task<void>`。  
  
### <a name="remarks"></a>备注  
 `when_all` 是生成 `task` 作为其结果的的非阻止函数。 与不同[task:: wait](task-class.md#wait)，则可以安全地中在 ASTA (应用程序 STA) 线程上的 UWP 应用中调用此函数。  
  
 如果一个任务被取消或引发异常，则返回的任务将提前，完成处于已取消状态，并且，如果遇到，将会引发该异常如果调用[task:: get](task-class.md#get)或`task::wait`该任务。  
  
 有关详细信息，请参阅[任务并行](../../../parallel/concrt/task-parallelism-concurrency-runtime.md)。  
  
##  <a name="when_any"></a>  when_any  
 创建一个任务，在作为自变量提供的任何任务成功完成后，此任务将成功完成。  
  
```
template<typename _Iterator>
auto when_any(
    _Iterator _Begin,
    _Iterator _End,
    const task_options& _TaskOptions = task_options()) 
    -> decltype (
        details::_WhenAnyImpl<
            typename std::iterator_traits<_Iterator>::value_type::result_type,
            _Iterator>::_Perform(_TaskOptions, _Begin, _End));

template<typename _Iterator>
auto when_any(
    _Iterator _Begin,
    _Iterator _End,
    cancellation_token _CancellationToken) 
       -> decltype (
           details::_WhenAnyImpl<
               typename std::iterator_traits<_Iterator>::value_type::result_type,
               _Iterator>::_Perform(_CancellationToken._GetImplValue(), _Begin, _End));
```   
  
### <a name="parameters"></a>参数  
 `_Iterator`  
 输入迭代器的类型。  
  
 `_Begin`  
 要合并到结果任务的元素范围中第一个元素的位置。  
  
 `_End`  
 超出要合并到结果任务的元素范围的第一个元素的位置。  
  
 `_TaskOptions`  
 `_CancellationToken`  
 控制返回的任务的取消的取消标记。 如果未提供取消标记，则结果任务将接收到导致任务完成的任务取消标记。  
  
### <a name="return-value"></a>返回值  
 在任意输入任务成功完成后成功完成的任务。 如果输入任务的类型为 `T`，则此函数的输出将为 `task<std::pair<T, size_t>>>`，其中的 pair 的第一个元素是正在完成的任务的结果，第二个元素是已完成的任务的索引。 如果输入任务的类型为 `void`，则输出为 `task<size_t>`，其中的结果是正在完成的任务的索引。  
  
### <a name="remarks"></a>备注  
 `when_any` 是生成 `task` 作为其结果的的非阻止函数。 与不同[task:: wait](task-class.md#wait)，则可以安全地中在 ASTA (应用程序 STA) 线程上的 UWP 应用中调用此函数。  
  
 有关详细信息，请参阅[任务并行](../../../parallel/concrt/task-parallelism-concurrency-runtime.md)。  
  
## <a name="see-also"></a>请参阅  
 [并发命名空间](concurrency-namespace.md)
