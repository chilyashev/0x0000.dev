<!--suppress HtmlUnknownTag -->
<template>
  <div>
    <div class="wrap">
    <pre class="console">mgc@{{host}}:~$ whoami
Mihail Chilyashev

</pre>
      <pre class="console">mgc@{{host}}:~$ whatis $(whoami)
A software developer.

</pre>
      <pre class="console">mgc@{{host}}:~$ ls -rt
web    mobile   java   spring_boot   a_whole_lot_more   résumé

</pre>
      <pre class="console">mgc@{{host}}:~$ cat résumé
<a href="https://chilyashev.com/cv" target="_blank">https://chilyashev.com/cv</a>
    </pre>
      <pre class="console cursor">mgc@{{host}}:~$ </pre>
    </div>
  </div>
</template>

<script>

  export default {
    components: {},
    data() {
      return {
        host: 'kernelshocked'
      }
    }
  }
</script>


<style>
  html,
  body {
    margin: 0 auto;
    height: 100%;
  }

  pre {
    padding: 0;
    margin: 0;
  }

  .wrap {
    margin: 0 auto;
    min-height: 100%;
    width: 100%;
  }

  .console {
    font-family: monospace;
    color: #fff;
    opacity: 0.8;
    font-size: 2em;
    overflow-y: auto;
    overflow-x: hidden;
    padding-top: 10px;
    padding-left: 20px;
  }

  @media (max-width: 1366px) {
    .console {
      font-size: 1em;
      overflow-x: auto;
    }
  }

  @media (min-width: 1466px) {
    .console {
      font-size: 1.8em;
    }
  }

  .console a {
    font-family: monospace;
    color: #fff;
    text-decoration: none;
  }

  .console a:hover {
    text-decoration: underline;
  }

  .cursor:after {
    content: "_";
    opacity: 1;
    animation: cursor 1s infinite;
  }

  @keyframes cursor {
    0% {
      opacity: 0;
    }
    40% {
      opacity: 0;
    }

    45% {
      opacity: 0.5;
    }

    50% {
      opacity: 1;
    }
    90% {
      opacity: 1;
    }

    95% {
      opacity: 0.5;
    }

    100% {
      opacity: 0;
    }
  }

</style>
