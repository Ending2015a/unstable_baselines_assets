<details>
<summary></summary>
dqn_discrete
digraph D {
    splines=false;
    bgcolor=white;
    node [shape=box, color=black, fontsize=12, height=0.1, width=0.1];
    obs[label="Observation"];
    subgraph cluster_cnn{
        label="Nature CNN";
        labeljust="l";
        graph[style=dotted];
        nature_cnn [shape=record, label="{Conv2D(32, 8, 4)|ReLU|Conv2D(64, 4, 2)|ReLU|Conv2D(32, 3, 1)|ReLU|Dense(512)|ReLU}"]
    }
    subgraph cluster_value{
        label="Q-Net";
        labeljust="l";
        graph[style=dashed];
        value_net [shape=record, label="Dense(Action space)"];
    }
    obs -> nature_cnn;
    nature_cnn:s-> value_net;
    value_net -> v;
    v[label="Q-value"]
}
dqn_discrete
</details>


<details>
<summary></summary>
dqn_continuous
digraph D {
    splines=false;
    bgcolor=white;
    node [shape=box, color=black, fontsize=12, height=0.1, width=0.1];
    obs[label="Observation"];
    subgraph cluster_mlp{
        label="MLP";
        labeljust="l";
        graph[style=dotted];
        mlp [shape=record, label="{Dense(64)|ReLU|Dense(64)|ReLU}"];
    }
    subgraph cluster_value{
        label="Q Net";
        labeljust="l";
        graph[style=dashed];
        value_net [shape=record, label="Dense(Action space)"];
    }
    obs -> mlp;
    mlp:s->value_net;
    value_net -> v;
    v[label="Q-value"]
}
dqn_continuous
</details>