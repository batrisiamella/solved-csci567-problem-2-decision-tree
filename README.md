Download Link: https://assignmentchef.com/product/solved-csci567-problem-2-decision-tree
<br>
Remember from lecture, we learned that we can use decision tree to solve classification and regression problem. Mostly we focus on classification. In problem 1 we used KNN to do classification. We could also use decision tree algorithm to do the same job. For Decision Tree, you will be asked to implement ID3 algorithm. It’s guaranteed that all features are discrete in this assignment. <strong>After finishing the implementation, you can use dt_test_script.py to test the correctness of your functions.</strong><a class="md-header-anchor " name="header-n187"></a>

<h3><a class="md-header-anchor " name="header-n10"></a>2.1.1 Information Gain</h3>

<ul>

 <li>In ID3 algorithm, we use Entropy to measure the uncertainty in the data set. We use Information Gain to measure the quality of a split.</li>

 <li>Entropy:</li>

 <li>Information_Gain:</li>

 <li>see more detail on <a href="https://urldefense.proofpoint.com/v2/url?u=https-3A__en.wikipedia.org_wiki_ID3-5Falgorithm&amp;d=DwMFaQ&amp;c=clK7kQUTWtAVEOVIgvi0NU5BOUHhpN0H8p7CSfnc_gI&amp;r=yYXh4HckzYFWw0_zu9Nv6g&amp;m=jSeQoESPLgNl7UYVyluLogJjjceJYUpB1D-AkAVjrc0&amp;s=IoqAGixMKM_zbRP7nTMwEnkZAniPWAzq6KM9c7931q8&amp;e=">ID3 Algorithm</a> In this section, you need to implement Information_Gain function on utils.py.</li>

</ul>

<h3><a class="md-header-anchor " name="header-n21"></a>2.1.2 Grow decision Tree and predict (25 points)</h3>

<ul>

 <li>In ID3 algorithm, we use the largest information gain to split the set S. Please consult the Lecture 2 notes page 23.</li>

</ul>

<ul>

 <li>Implement TreeNode split function and TreeNode predict function in hw1_dt.py:

  <ul>

   <li>TreeNode.split

    <ul>

     <li>In TreeNode class, variable features represents all data points in current TreeNode. Variable labels represents corresponding labels for all data points. Variable children is a list of TreeNode after split the current node on best attribute. This should be a recursive process that once we call the split function, the TreeNode will keep spliting until we get the whole decision tree.</li>

     <li><strong>When there is a tie of information gain on comparing all attributes of current TreeNode, always choose the attribute which has more attribute values. If they have same number of attribute values, use the one with small index.</strong></li>

     <li><strong>Build child list of each TreeNode with increasing order on attribute values, the order matters because it will be used when comparing two decision trees.</strong></li>

    </ul></li>

  </ul>

  <ul>

   <li>TreeNode.predict

    <ul>

     <li>This function will be called once you have got the decision tree. It will take one single data point as a parameter, your code should process that data point and go through your tree to a leaf node and make prediction. This function should return a predicted lable.</li>

    </ul></li>

  </ul></li>

</ul>

<ul>

 <li>You don’t need to implement Decision Tree predict and train function in hw1_dt.py. We will provide these two function in the statercode. Reading the train and predict function would help you understand functions that you need to implement.

  <ul>

   <li>DecisionTree.train</li>

   <li>DecisionTree.predict</li>

  </ul></li>

 <li>This is the comarision logic we will use to check your decision tree.</li>

</ul>

<h2><a class="md-header-anchor " name="header-n59"></a>Part 2.2 Pruning Decision Tree</h2>

Sometimes, in order to prevent overfitting. We need to prune our Decision Tree. There are several approaches to avoid overfitting in building decision trees.

<ul>

 <li>Pre-pruning: stop growing the tree earlier, before it perfectly classifies the training set.</li>

 <li>Post-pruning: grows decision tree completely on training set, and then post prune decision tree.</li>

</ul>

Practically, the second approach post-pruning is more useful, also it is not easy to precisely estimate when to stop growing the tree by using pre-pruning. We will use Reduced Error Pruning, as one of Post-pruning in this assignment.

For Pruning of Decision Tree, you can refer <a href="https://urldefense.proofpoint.com/v2/url?u=http-3A__jmvidal.cse.sc.edu_talks_decisiontrees_reducederrorprun.html-3Fstyle-3DWhite&amp;d=DwMFaQ&amp;c=clK7kQUTWtAVEOVIgvi0NU5BOUHhpN0H8p7CSfnc_gI&amp;r=yYXh4HckzYFWw0_zu9Nv6g&amp;m=jSeQoESPLgNl7UYVyluLogJjjceJYUpB1D-AkAVjrc0&amp;s=m8oZfwPt7lK7dHjzo71WBzdiYIu22fIBn7h4KHwRvF4&amp;e=">Reduce Error Pruning</a> and P69 of Textbook: Machine Learning -Tom Mitchell.

<h3><a class="md-header-anchor " name="header-n69"></a>2.2.1 Reduce Error Pruning</h3>

<strong>Hint: in this part, you can add other parameters or functions in TreeNode class and DecisionTree class to help you in pruning the decision tree. But your changes should not influence results of previous parts.</strong> Implement the reduced_error_pruning function in util.py.

Good Luck! &#x1f642;

<span class="kksr-muted">Rate this product</span>

<pre></pre>

<pre class=" CodeMirror-line " role="presentation"><span role="presentation"># calculate information_gain according to branches seperated by one feature</span></pre>

<pre class=" CodeMirror-line " role="presentation"><span role="presentation"># input:</span></pre>

<pre class=" CodeMirror-line " role="presentation"><span role="presentation">    -branches: List[List[int]] num_attribute_values*num_classes : Count of data points belonging to each attribute and class. </span></pre>

<pre class=" CodeMirror-line " role="presentation"><span role="presentation">def Information_Gain(S, branches):</span></pre>

<pre class=" CodeMirror-line " role="presentation"><span role="presentation">    -S: float Entropy of current state</span></pre>

<pre class=" CodeMirror-line " role="presentation"><span role="presentation">    e.g. [[1,2],[1,1][2,0]] represents there are three attribute values. For attribute 0, there is one data point that belongs to class 0 and two data points that belong to class 1.</span></pre>

<pre class=" CodeMirror-line " role="presentation"><span role="presentation"># return: float</span></pre>

<pre></pre>

<pre class=" CodeMirror-line " role="presentation"><span role="presentation">    if dTree_node.splittable != my_dTree_node.splittable:</span></pre>

<pre class=" CodeMirror-line " role="presentation"><span role="presentation">    if dTree_node.cls_max != my_dTree_node.cls_max:</span></pre>

<pre class=" CodeMirror-line " role="presentation"><span role="presentation">    if dTree_node.splittable:</span></pre>

<pre class=" CodeMirror-line " role="presentation"><span role="presentation">            return False</span></pre>

<pre class=" CodeMirror-line " role="presentation"><span role="presentation">        for idx, child in enumerate(dTree_node.children):</span></pre>

<pre class=" CodeMirror-line " role="presentation"><span role="presentation">            if not compareDecisionTree(child, my_dTree_node.children[idx]):</span></pre>

<pre class=" CodeMirror-line " role="presentation"><span role="presentation">    return True</span></pre>

<pre class=" CodeMirror-line " role="presentation"><span role="presentation">def compareDecisionTree(dTree_node, my_dTree_node):</span></pre>

<pre class=" CodeMirror-line " role="presentation"><span role="presentation">        return False</span></pre>

<pre class=" CodeMirror-line " role="presentation"><span role="presentation">        return False</span></pre>

<pre class=" CodeMirror-line " role="presentation"><span role="presentation">        if len(dTree_node.children) != len(my_dTree_node.children):</span></pre>

<pre class=" CodeMirror-line " role="presentation"><span role="presentation">                return False</span></pre>

<pre></pre>

<pre class=" CodeMirror-line " role="presentation"><span role="presentation">0. Split data into training and validation sets.</span></pre>

<pre class=" CodeMirror-line " role="presentation"><span role="presentation">1. Grow the decision tree until further pruning is harmful:</span></pre>

<pre class=" CodeMirror-line " role="presentation"><span role="presentation">2. Evaluate decision tree on validation dataset.</span></pre>

<pre class=" CodeMirror-line " role="presentation"><span role="presentation">Reduced Error Pruning</span></pre>

<pre class=" CodeMirror-line " role="presentation"><span role="presentation">3. Greedily remove TreeNode (from leaf to root) that most improves prediction accuracy on validation set.</span></pre>

<pre></pre>

<pre class=" CodeMirror-line " role="presentation"><span role="presentation"># input: </span></pre>

<pre class=" CodeMirror-line " role="presentation"><span role="presentation">def reduced_error_pruning(decitionTree):</span></pre>

<pre class=" CodeMirror-line " role="presentation"><span role="presentation">    - decitionTree: decitionTree trained based on training data set.</span></pre>

<pre class=" CodeMirror-line " role="presentation"><span role="presentation">    - X_test: List[List[any]] test data, num_cases*num_attributes</span></pre>

<pre class=" CodeMirror-line " role="presentation"><span role="presentation">    - y_test: List[any] test labels, num_cases*1</span></pre>