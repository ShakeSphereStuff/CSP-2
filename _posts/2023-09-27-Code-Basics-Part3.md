<p id = "theResult">Hello World</p>
<button onclick="load()">Test</button>
<script>
    var steps = 0;
    var periods = ".";
    var data = [{
        "x":1,
        "y":0
    },
    {
        "x":2,
        "y":0
    },
    {
        "x":3,
        "y":0
    },
    {
        "x":4,
        "y":0
    },
    {
        "x":5,
        "y":0
    },
    {
        "x":6,
        "y":0
    },
    {
        "x":7,
        "y":0
    },
    {
        "x":8,
        "y":0
    },
    {
        "x":9,
        "y":0
    },
    {
        "x":10,
        "y":0
    },
    {
        "x":11,
        "y":0
    },
    {
        "x":12,
        "y":0
    },
    {
        "x":13,
        "y":0
    },
    {
        "x":14,
        "y":0
    },
    {
        "x":15,
        "y":0
    },
    {
        "x":16,
        "y":0
    },
    {
        "x":17,
        "y":0
    },
    {
        "x":18,
        "y":0
    },
    {
        "x":19,
        "y":0
    },
    {
        "x":20,
        "y":0
    },
    {
        "x":20,
        "y":1
    },
    {
        "x":20,
        "y":2
    },
    {
        "x":20,
        "y":3
    },
    {
        "x":20,
        "y":4
    },
    {
        "x":20,
        "y":5
    }];
    var result = document.getElementById("theResult")
    function load(){
        if(steps < data.length && data[steps]["y"] == 0){
            result.innerHTML = "Hello World" + periods.repeat(data[steps]["x"])
            steps += 1
        }
        else if(steps < data.length - 0){
            periods = "....................<br>" 
            result.innerHTML = "Hello World" + periods.repeat(data[steps]["y"])
            console.log(periods)
            steps += 1
        }
        console.log(steps)
    }
</script>