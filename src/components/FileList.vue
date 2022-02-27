<template>
  <div class="track-list">
    <div :style="listStyles">
      <FileListItem
        v-for="(track, index) in sourceData"
        :key="itemKey === 'id' ? track.id : `${track.id}${index}`"
        :track-prop="track"
        :highlight-playing-track="true"
        @dblclick.native="dblclick()"
        @click.right.native="openMenu($event, track, index)"
      />
    </div>
  </div>
</template>

<script>
import FileListItem from '@/components/FileListItem';

export default {
  name: 'FileList',
  components: {
    FileListItem,
  },
  props: {
    sourceData: {
      type: Array,
      default: () => {
        return [];
      },
    },
    id: {
      type: Number,
      default: 0,
    },
    itemKey: {
      type: String,
      default: 'id',
    },
  },
  data() {
    return {
      rightClickedTrack: {
        id: 0,
        name: '',
        ar: [{ name: '' }],
        al: { picUrl: '' },
      },
      rightClickedTrackIndex: -1,
      listStyles: {
        display: 'grid',
        gap: '4px',
        gridTemplateColumns: `repeat(${this.columnNumber}, 1fr)`,
      },
    };
  },
  computed: {},
  created() {},
  methods: {
    dblclick() {
      console.log('dblclick');
    },
    openMenu() {
      console.log('openMenu');
    },
  },
};
</script>

<style lang="scss" scoped></style>
