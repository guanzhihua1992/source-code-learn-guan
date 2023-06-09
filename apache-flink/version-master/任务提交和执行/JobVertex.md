JobGraph图结构中的单个节点通过JobVertex表示.JobVertex主 要包含JobEdge和IntermediateDataSet等结构以及与节点相关的配置 和运行资源等信息。
JobVertex结构的主要组成部分如下
·JobVertexID:存储当前JobVertex节点的ID信息。
·idAlternatives:Vertex中的替代ID，如果JobVertexID重复了，可 以使用该列表中的ID。
·operatorIDs:包含当前Vertex中所有Operator的唯一ID集合。
·results:当前Vertex对应的中间结果数据集，通过 IntermediateDataSet表示。
·inputs:当前Vertex所有的输入边集合，通过JobEdge表示。
·parallelism:当前Vertex节点对应的并行度参数。
·invokableClassName:当前Vertex对应的invokableClassName，即 Operator对应的ClassName，在Task运行的过程中，会通过 invokableClassName进行对应Operator的初始化与执行。
·slotSharingGroup:Vertex中Slot共享组配置，该配置允许Job节点 中的SubTask运行在同一个Slot中。
·operatorName:当前Vertex节点Operator的名称。
·inputDependencyConstraint:表示当前Vertex节点中Task被调度的 输入依赖约束，其中ANY表示一旦有输入节点可以消费，就立即对当 前JobVertex的Task进行调度执行;ALL表示只有当所有的输入节点全部 可消费时，才能调度当前节点对应的Task任务。