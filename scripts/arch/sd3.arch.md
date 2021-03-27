<details>
<summary></summary>
sd3_arch
digraph D {
    splines=false;
    node [shape=box, color=black, fontsize=12, height=0.1, width=0.1];
    input1[label="Observation"];
    input2[shape=record, label="Observation|Action"];
    subgraph cluster_actor{
        label="Actor";
        labeljust="l";
        graph[style=dotted];
        actor [shape=record, label="{Dense(400)|ReLU|Dense(300)|ReLU|Dense(Action space)|Tanh}"]
    }
    subgraph cluster_critic{
        label="Critic";
        labeljust="l";
        graph[style=dotted];
        critic [shape=record, label="{Dense(400)|ReLU|Dense(300)|ReLU|Dense(1)}"]
    }    
    input1 -> actor:n;
    input2 -> critic:n;
    actor:s -> pi;
    critic:s -> v;
    pi[label="Action"];
    v[label="Value"]
}
sd3_arch
</details>