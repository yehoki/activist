<template>
  <div
    class="flex flex-col px-4 xl:px-8 text-light-text dark:text-dark-text bg-light-content dark:bg-dark-content"
  >
    <Head>
      <Title>{{ event.name }}</Title>
    </Head>
    <HeaderAppPage :event="event">
      <BtnLabeled
        :cta="true"
        linkTo="/"
        :label="$t('components.btn-labeled.offer-to-help')"
        fontSize="base"
        rightIcon="bi:arrow-right"
        iconSize="1.25em"
        :alternateText="$t('components.btn-labeled.offer-to-help-aria-label')"
      />
      <BtnLabeled
        :cta="true"
        linkTo="/"
        :label="$t('components.btn-labeled.support')"
        fontSize="base"
        leftIcon="IconSupport"
        iconSize="1.25em"
        :counter="event.supporters"
        :alternateText="$t('components.btn-labeled.support-event-aria-label')"
      />
      <BtnLabeled
        :cta="true"
        linkTo="/"
        :label="$t('components.btn-labeled.share-event')"
        fontSize="base"
        leftIcon="bi:box-arrow-up"
        iconSize="1.25em"
        :alternateText="$t('components.btn-labeled.share-event-aria-label')"
      />
    </HeaderAppPage>
    <div class="pb-6 space-y-6">
      <div
        class="pb-6 grid grid-rows-2 grid-cols-1 lg:grid-cols-3 lg:grid-rows-1 space-y-6 lg:pb-0 lg:space-y-0 lg:space-x-6 lg:mr-6"
      >
        <CardAbout aboutType="event" :event="event" class="lg:col-span-2" />
        <MediaMap
          class="w-full h-full"
          v-if="event.inPersonLocation"
          :addresses="[event.inPersonLocation]"
          :type="event.type"
          :title="event.name"
        />
      </div>
      <CardGetInvolved
        :event="event"
        disclaimer="Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam erat, sed diam voluptua. At vero eos et accusam et justo duo dolores et ea rebum. Stet clita kasd gubergren, no sea takimata sanctus est Lorem ipsum dolor sit amet. Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam erat, sed diam voluptua. At vero eos et accusam et justo duo dolores et ea rebum. Stet clita kasd gubergren, no sea takimata sanctus est Lorem ipsum dolor sit amet."
      />
      <CardConnect :social-links="event.socialLinks" :userIsAdmin="true" />
    </div>
  </div>
</template>

<script setup lang="ts">
import type { Event } from "../../../types/event";

definePageMeta({
  layout: "sidebar",
});

const { id } = useRoute().params;

const event: Event = {
  name: "Brandenburg Gate Climate Demo",
  tagline: "There is no Planet B",
  organizer: "Berlin Climate Org",
  type: "act",
  topic: "Environment",
  description:
    "Aute aliqua reprehenderit ex ut commodo nostrud et excepteur. Sunt amet velit sunt fugiat et excepteur dolore pariatur nisi non. Exercitation aute aute culpa commodo commodo ea Lorem aliquip id duis. Laboris nostrud ullamco ea voluptate et anim id adipisicing sint reprehenderit incididunt elit. Est fugiat pariatur elit culpa in incididunt eu esse cupidatat minim. Deserunt duis culpa minim Lorem consectetur quis fugiat ipsum nostrud voluptate veniam do. Reprehenderit duis officia in enim anim elit.",
  getInvolvedDescription:
    "Sint cillum excepteur sint cupidatat do consectetur excepteur nisi veniam. Sint id in sit eiusmod Lorem commodo minim culpa id cupidatat consectetur. Labore nisi est officia sunt occaecat.",
  inPersonLocation: "Brandenburg Gate, Berlin",
  date: new Date().toISOString().slice(0, 10),
  supporters: 30,
  imageURL: "/images/tech-from-below.svg",
  socialLinks: ["climate_org@mastodon", "climate_org@email.com"],
};
</script>
