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
</style>
