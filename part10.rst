.. _part10:

***************************
Building the HTML Frontend
***************************

We will be using the JS library eztz for our frontend, this allows you to easily interact with your Tezos smart contract by reading state, storage and write transactions. To simplify this tutorial, we included HTML code below:

.. code-block:: html

  <!DOCTYPE html>
  <html>
  <head>
    <title>My first dApp</title>
    <link href='https://fonts.googleapis.com/css?family=Open+Sans:400,700' rel='stylesheet' type='text/css'>
    <link href='https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css' rel='stylesheet' type='text/css'>
    <script src="https://code.jquery.com/jquery-3.1.1.slim.min.js"></script>
    <script src="./eztz.min.js"></script>
    <script src="./app.js"></script>
  </head>
  <body class="container">
    <h1>A Simple Voting Application on Tezos Blockchain</h1>
    <div>Your account <strong><span id="account"></span></strong> has balance: <strong>NADA <span id="balance"></span></strong></div>
    <br>
    <div class="table-responsive">
      <table class="table table-bordered">
        <thead>
          <tr>
            <th>Candidate</th>
            <th>Votes</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td>Alice</td>
            <td id="candidate-1"></td>
          </tr>
          <tr>
            <td>Bob</td>
            <td id="candidate-2"></td>
          </tr>
          <tr>
            <td>Mary</td>
            <td id="candidate-3"></td>
          </tr>
        </tbody>
      </table>
    </div>
    <input type="text" id="candidate" />
    <a href="#" onclick="voteForCandidate()" class="btn btn-primary">Vote</a>
    <br>
    <br>
    <div id="msg"></div>
    <script>
      $(function() {
        loadData();
      });
    </script>
    </body>
  </html>

In the header, we call the eztz library, jquery and bootstrap for some CSS styling. Regarding functionality, we have a JS function called voteForCandidate which we will define later. We also have code to display Tez balance and a JS function called loadData, which on page load, will query the blockchain for the up-to-date voting information. For this tutorial, the candidate names are hard coded, but feel free to build a dynamic version later!

In your current directory, you should have the following files:

Index.html
App.js (empty)
eztz.min.js

The eztz library can be downloaded here: https://github.com/TezTech/eztz/blob/master/dist/eztz.min.js

If you load up index.html it should look like this:

:ref:`part11`.
