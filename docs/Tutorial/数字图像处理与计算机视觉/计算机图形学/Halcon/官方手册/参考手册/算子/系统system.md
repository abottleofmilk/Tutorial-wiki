## 计算设备 Compute Devices

- [`activate_compute_device`]

  激活计算设备。

- [`deactivate_all_compute_devices`]

  停用所有计算设备。

- [`deactivate_compute_device`]

  停用计算设备。

- [`get_compute_device_info`]

  获取有关计算设备的信息。

- [`get_compute_device_param`]

  查询计算设备参数。

- [`init_compute_device`]

  初始化计算设备。

- [`open_compute_device`]

  打开计算设备。

- [`query_available_compute_devices`]

  获取可用计算设备的列表。

- [`release_all_compute_devices`]

  关闭所有计算设备。

- [`release_compute_device`]

  关闭 compute_device。

- [`set_compute_device_param`]

  设置计算设备的参数。

## 数据库 Database

- [`count_relation`]

  HALCON 数据库中的条目数。

- [`get_modules`]

  查询使用的模块和模块密钥。

- [`reset_obj_db`]

  为标志性物体重置 HALCON 系统。

## 错误处理 Error Handling

- [`get_check`]

  HALCON 控制模式的状态。

- [`get_error_text`]

  查询一个HALCON错误号的错误文本。

- [`get_extended_error_info`]

  返回调用线程的最后一个 HALCON 错误的扩展错误信息。

- [`get_spy`]

  HALCON 调试工具的当前配置。

- [`query_spy`]

  查询 HALCON 调试工具的可能设置。

- [`set_check`]

  激活和停用 HALCON 控制模式。

- [`set_spy`]

  HALCON 调试工具的控制。

## 输入/输出设备 I/O Devices

- [`close_io_channel`]

  关闭 I/O 通道。

- [`close_io_device`]

  关闭指定的 I/O 设备。

- [`control_io_channel`]

  对 I/O 通道执行操作。

- [`control_io_device`]

  对 I/O 设备执行操作。

- [`control_io_interface`]

  在 I/O 接口上执行操作。

- [`get_io_channel_param`]

  查询I/O通道的具体参数。

- [`get_io_device_param`]

  查询 I/O 设备实例的设置。

- [`open_io_channel`]

  打开并配置 I/O 通道。

- [`open_io_device`]

  打开并配置 I/O 设备。

- [`query_io_device`]

  查询指定 I/O 设备的通道信息。

- [`query_io_interface`]

  查询指定I/O设备接口的信息。

- [`read_io_channel`]

  从指定的 I/O 通道读取一个值。

- [`set_io_channel_param`]

  设置 I/O 通道的具体参数。

- [`set_io_device_param`]

  配置特定的 I/O 设备实例。

- [`write_io_channel`]

  将值写入指定的 I/O 通道。

## 信息 Information

- [`get_chapter_info`]

  获取有关运算符章节的信息。

- [`get_keywords`]

  获取分配给操作员的关键字。

- [`get_operator_info`]

  获取有关 HALCON 运算符的信息。

- [`get_operator_name`]

  获取将给定字符串作为其名称的子字符串的运算符。

- [`get_param_info`]

  获取有关运算符参数的信息。

- [`get_param_names`]

  获取 HALCON 运算符的参数名称。

- [`get_param_num`]

  获取 HALCON 运算符的不同参数类的数量。

- [`get_param_types`]

  获取 HALCON 运算符的控制参数的默认数据类型。

- [`query_operator_info`]

  与运营商有关的信息查询槽。[`get_operator_info`]

- [`query_param_info`]

  运营商在线信息查询槽。[`get_param_info`]

- [`search_operator`]

  搜索分配给一个关键字的所有运算符的名称。

## 多线程 Multithreading

- [`broadcast_condition`]

  向条件同步对象发出信号。

- [`clear_barrier`]

  销毁屏障同步对象。

- [`clear_condition`]

  销毁条件同步对象。

- [`clear_event`]

  清除事件同步对象。

- [`clear_message`]

  关闭消息句柄并释放所有相关资源。

- [`clear_message_queue`]

  关闭消息队列句柄并释放所有相关资源。

- [`clear_mutex`]

  清除互斥锁同步对象。

- [`create_barrier`]

  创建屏障同步对象。

- [`create_condition`]

  创建条件变量同步对象。

- [`create_event`]

  创建事件同步对象。

- [`create_message`]

  创建一个新的空消息。

- [`create_message_queue`]

  创建一个新的空消息队列。

- [`create_mutex`]

  创建互斥同步对象。

- [`dequeue_message`]

  从消息队列中接收一条或多条消息。

- [`enqueue_message`]

  将一条或多条消息加入消息队列。

- [`get_current_hthread_id`]

  返回当前线程的 HALCON 线程 ID。

- [`get_message_obj`]

  从消息中检索与密钥关联的对象。

- [`get_message_param`]

  查询消息参数或有关消息的信息。

- [`get_message_queue_param`]

  查询消息队列参数或队列信息。

- [`get_message_tuple`]

  从消息中检索与密钥关联的元组。

- [`get_threading_attrib`]

  查询线程/同步对象的属性。

- [`interrupt_operator`]

  尝试中断在不同线程中运行的运算符。

- [`lock_mutex`]

  锁定互斥锁同步对象。

- [`read_message`]

  从文件中读取消息。

- [`set_message_obj`]

  将键/对象对添加到消息中。

- [`set_message_param`]

  在消息上设置消息参数或调用命令。

- [`set_message_queue_param`]

  设置消息队列参数或调用队列上的命令。

- [`set_message_tuple`]

  将密钥/元组对添加到消息中。

- [`signal_condition`]

  向条件同步对象发出信号。

- [`signal_event`]

  解锁事件同步对象。

- [`timed_wait_condition`]

  有界等待条件同步对象的信号。

- [`try_lock_mutex`]

  锁定互斥锁同步对象。

- [`try_wait_event`]

  仅在事件同步对象解锁时锁定它。

- [`unlock_mutex`]

  解锁互斥锁同步对象。

- [`wait_barrier`]

  等待屏障同步对象的释放。

- [`wait_condition`]

  等待条件同步对象的信号。

- [`wait_event`]

  锁定事件同步对象。

- [`write_message`]

  将消息写入文件。

## 操作系统 Operating System

- [`count_seconds`]

  过去的时间。

- [`get_system_time`]

  读出系统时间。

- [`system_call`]

  执行系统命令。

- [`wait_seconds`]

  延迟程序的执行。

## 并行 Parallelization

- [`get_aop_info`]

  返回运算符的 AOP 信息。

- [`optimize_aop`]

  检查硬件，了解其自动运算符并行化的潜力。

- [`query_aop_info`]

  操作符查询AOP信息的索引结构。

- [`read_aop_knowledge`]

  加载有关自动运算符并行化的硬件相关行为的知识。

- [`set_aop_info`]

  为运算符设置 AOP 信息。

- [`write_aop_knowledge`]

  将有关自动运算符并行化的硬件相关行为的知识写入文件。

## 参数 Parameters

- [`get_system`]

  获取 HALCON 系统参数的当前值。

- [`get_system_info`]

  无需许可证即可获取系统信息的当前值。

- [`set_operator_timeout`]

  为操作员设置超时。

- [`set_system`]

  设置 HALCON 系统参数。

## 序列化 Serial

- [`clear_serial`]

  清除串行连接的缓冲区。

- [`close_serial`]

  关闭串行设备。

- [`get_serial_param`]

  获取串口设备的参数。

- [`open_serial`]

  打开串行设备。

- [`read_serial`]

  从串行设备读取。

- [`set_serial_param`]

  设置串口设备的参数。

- [`write_serial`]

  写入串行连接。

## 序列化迭代 Serialized Item

- [`clear_serialized_item`]

  删除序列化项目。

- [`create_serialized_item_ptr`]

  创建序列化项目。

- [`fread_serialized_item`]

  从文件中读取序列化项目。

- [`fwrite_serialized_item`]

  将序列化项目写入文件。

- [`get_serialized_item_ptr`]

  访问序列化项目的数据指针。

## 套接字 Sockets

- [`close_socket`]

  关闭套接字。

- [`get_next_socket_data_type`]

  确定下一个套接字数据的 HALCON 数据类型。

- [`get_socket_descriptor`]

  获取操作系统使用的套接字的套接字描述符。

- [`get_socket_param`]

  获取套接字参数的值。

- [`open_socket_accept`]

  打开一个接受连接请求的套接字。

- [`open_socket_connect`]

  打开一个套接字并将其连接到接受套接字。

- [`receive_data`]

  使用通用套接字连接从外部设备或应用程序接收任意数据。

- [`receive_image`]

  通过套接字连接接收图像。

- [`receive_region`]

  通过套接字连接接收区域。

- [`receive_serialized_item`]

  通过套接字连接接收序列化项目。

- [`receive_tuple`]

  通过套接字连接接收元组。

- [`receive_xld`]

  通过套接字连接接收 XLD 对象。

- [`send_data`]

  使用通用套接字通信将任意数据发送到外部设备或应用程序。

- [`send_image`]

  通过套接字连接发送图像。

- [`send_region`]

  通过套接字连接发送区域。

- [`send_serialized_item`]

  通过套接字连接发送序列化项目。

- [`send_tuple`]

  通过套接字连接发送元组。

- [`send_xld`]

  通过套接字连接发送 XLD 对象。

- [`set_socket_param`]

  设置套接字参数。

- [`socket_accept_connect`]

  在协议类型为//的侦听套接字上接受连接 请求。*`'HALCON'`**`'TCP'`**`'TCP4'`**`'TCP6'`*