<!-- Blog: Coding Problems -->
<template>
  <section>
    <AppCodeSolutionCard
      v-for="(solution, index) in codeSolutions"
      :key="index"
      :problemTitle="solution.title"
      :url="solution._path"
      :tags="solution.tags"
      :problemUrl="solution.problemUrl"
    />
  </section>
</template>

<script setup>
  definePageMeta({
    layout: "blog-list-layout"
  });

  // Fetch all LeetCode solutions
  const { data: codeSolutions } = await useAsyncData("leetcode", () =>
    queryContent("/")
      .where({ _dir: { $eq: "leetcode" } })
      .find()
  );

  // console.log(JSON.parse(JSON.stringify(codeSolutions.value)));
</script>
