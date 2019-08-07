<style src="./annotationLayer.css"></style>
<script>

	import componentFactory from './componentFactory'
	import pdfjsWrapper from './pdfjsWrapper'

	var PDFJS = pdfjsLib;

	if ( process.env.VUE_ENV !== 'server' ) {

		if ( typeof window !== 'undefined' && 'Worker' in window ) {

			var PdfjsWorker =PdfjsWorker;
			PDFJS.GlobalWorkerOptions.workerPort = new PdfjsWorker();
		}
	}

	var component = componentFactory(pdfjsWrapper(PDFJS));
	component.PDFJS = PDFJS;

	export default component;

</script>