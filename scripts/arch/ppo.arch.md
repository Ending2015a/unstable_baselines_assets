<details>
<summary></summary>
ppo_discrete
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
    subgraph cluster_policy{
        label="Policy";
        labeljust="l";
        graph[style=dashed];
        policy_net [shape=record, label="Dense(Action space)"];
    }
    subgraph cluster_value{
        label="Value";
        labeljust="l";
        graph[style=dashed];
        value_net [shape=record, label="Dense(1)"];
    }
    obs -> nature_cnn;
    nature_cnn:s->{policy_net, value_net};
    policy_net -> pi;
    value_net -> v;
    pi[label="Action"];
    v[label="Value"]
}
ppo_discrete
</details>